---
layout: post
title: "left associative parser"
date: 2016-02-16 22:05:29
categories: ["haskell"]
tags: []
---

We can simply modify a left recursive grammar and write a recursive
descent parser to parse. But it may change the operator associativity. See [wikipedia][left_rec] for more details.

A simple possible solution is to parse as much as possible terms instead of make a recursive call. Such as for the following grammar:

```
<expr> := <expr> [+-] number
        | number
```

We modify it to non-left recursive:

```
<expr>  := number <expr'>
<expr'> := [+-] number <expr'>
         | eps
```

Then we can parse `[+-] number` part as much as possible, then
put it all together. See the following code for more details.

```haskell
import Text.ParserCombinators.Parsec

data Expr = Op Char Expr Expr
          | Num Int

instance Show Expr where
    show (Op op e1 e2) = "(" ++ show e1 ++ " " ++ [op] ++ " " ++ show e2 ++ ")"
    show (Num n) = show n

parseExpr :: Parser Expr
parseExpr = do
    num <- parseNum
    es <- many parseExpr'
    return $ foldl (\a b -> b a) num es

parseExpr' :: Parser (Expr -> Expr)
parseExpr' = do
    op <- oneOf "+-"
    num <- parseNum
    return $ \x -> Op op x num

parseNum :: Parser Expr
parseNum = many1 digit >>= return . Num . read

test :: String -> IO ()
test s = case parse parseExpr "" s of
    Left _ -> print "parse error!"
    Right e -> print e

main :: IO ()
main = do
    test "1+2+3"         -- ((1 + 2) + 3)
    test "1-2-3"         -- ((1 - 2) - 3)
    test "1+2-3-4+5-6-7" -- ((((((1 + 2) - 3) - 4) + 5) - 6) - 7)
```

This is not the universal way to maintain operand associativity, but it is simple to write for some simple grammar.

There is a lot of parse techs to learn.




[left_rec]: https://en.wikipedia.org/wiki/Left_recursion
