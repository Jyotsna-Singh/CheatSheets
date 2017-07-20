# Chapter - 3 Strategy

## Index

[Introduction](#introduction)

[3.1 - Iteration](#31---iteration)

[3.2 - Recursion](#32---recursion)

[3.3 - Brute Force](#33---bruteforce)

[3.4 - Backtracking](#34---backtracking)

[3.5 - Heuristics](#35---heuristics)

[3.6 - Divide & Conquer](#36---divide&conquer)

[3.7 - Dynamic Programming](#37---dynamicprogramming)

[3.8 - Branch & Bound](#38---branch&bound)


## Introduction
Excelling at problem solving requires being a good strategist. Following are the strategies for algorithm desgin.
    
## 3.1 - Iteration
Iterative strategy consists of using loops (*for*, *while*) to repeat a process until a condition is met. Each step in a loop is called an iteration.

Running thought an input and applying the same operations on every part of it.

Example: Fish Reunion 
Given : Alphabetically sorted 2 lists of -saltwater fish & -freshwater fish. 
To-Do : Create a list featuring all the fish in alphabetical order.

    function merge(sea, fresh)
        result <- List.new
        
        while not (sea.empty and fresh.empty)
            if sea.top_item > fresh.top_item
                fish <- sea.remove_top_item
            else
                fish <- fresh.remove_top_item
            result.append(fish)
            
        return result

Complexity: *O(n)*

## 3.2 - Recursion

## 3.3 - Brute Force

## 3.4 - Backtracking

## 3.5 - Heuristics

## 3.6 - Divide & Conquer

## 3.7 - Dynamic Programming

## 3.8 - Branch & Bound

