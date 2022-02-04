---
title: "(WIP draft) Haskell numeric classes"
author: Jens Petersen
date: Feb 4, 2022
tags: [haskell]
description: Summary about the Haskell Numeric type classes
---

I have often found Haskell's various Num type-classes a little confusing.
So I thought I would write a short summary to help myself and hopefully others
to make it clearer.

## Table of Numeric classes from the Prelude

| Super =>         | Class         | property                      |
|:----------------:|:--------------|:------------------------------|
|                  | `Num a`       |`fromInteger :: Integer -> a`  |
|`Num, Ord =>`     | `Real a`      |`toRational :: a -> Rational`  |
|`Real, Enum =>`   | `Integral a`  |`toInteger :: a -> Integer`    |
|`Num =>`          | `Fractional a`|`fromRational :: Rational -> a`|
|`Fractional =>`   | `Floating a`  |`exp`, `log`, `sin`, `cosh`, ...|
|`Fractional =>`   |`RealFrac a`|`properFraction :: Integral b => a -> (b, a)`|
|`Floating,RealFrac =>`|`RealFloat a`|`decodeFloat :: a -> (Integer, Int)`|

(`type Rational = Ratio Integer`)

## Other Numeric types

`Complex`

`Ratio a`

`Fixed a`
