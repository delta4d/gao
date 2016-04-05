---
layout: post
title: "left associative parser"
date: 2016-04-05 11:35:28
categories: ["haskell"]
tags: []
---

I learned a new tech to make left associative parser in parsec recently.
It is very "easy" by using [chainl1][].

[chainl1]: http://hackage.haskell.org/package/parsec-3.1.9/docs/Text-Parsec-Combinator.html#v:chainl1

`chainl1 x op` means many `x` chained with `op`, resulting `((x1 op x2) op x3)...`.
Just like `((1+2)+3)+...`, so if `x` is of type `Parser a`, then `op` is of type
`Parser (a -> a -> a)`.

If we want to parse arithmetic expression with operation "+-\*/" and
parentheses. Then first separates expression with `+-`, then in each term,
they are bind with `*/`, then down to the atom type, which is an integer, or
another expression with parentheses. Look at the following code for more details.

```haskell
import Text.ParserCombinators.Parsec

int :: Parser Int
int = many1 digit >>= return . read

pare :: Parser Int -> Parser Int
pare e = char '(' *> e <* char ')'

expr = term `chainl1` add_op
term = factor `chainl1` mul_op
factor = pare expr <|> int

add_op =  (char '+' >> return (+))
      <|> (char '-' >> return (-))

mul_op =  (char '*' >> return (*))
      <|> (char '/' >> return (div))

parse_expr e = case parse expr "" e of
    Left _  -> -111111
    Right x -> x

main = do
    print $ parse_expr "1-(2-3)"        -- => 2
    print $ parse_expr "1-2-3-4"        -- => -8
    print $ parse_expr "1-2*3+4*5"      -- => 15
    print $ parse_expr "1-2*3+4*5/2/2"  -- => 0
```

Now I still build parser by hand with parsec basics, still have much much to learn.
