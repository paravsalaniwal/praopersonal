---
toc: true
comments: true
layout: post
title: Frontend Progress
type: tangibles
courses: { csa: {week: 14} }
---

# December 11, 2023

# Frontend Progress

## Fetch function 1 (displaying each stock's data, no sorting)

<img width="507" alt="image" src="https://github.com/paravsalaniwal/praopersonal/assets/111609656/da6304ef-9ec5-475a-8814-7aa0cb6f59f3">

This fetch function is used to call in the DailyStocks endpoint of the API which then gets the ID of the month based on the button the user selects and displays that graph.

## Fetch function 2 (displaying graphs in sorted order)

<img width="697" alt="image" src="https://github.com/paravsalaniwal/praopersonal/assets/111609656/476b4589-801c-4586-9fe6-0ccef0214450">

This fetch function is used to call in the monthly-stocks/{sorting-way} API in which depending on the type of sorting the user selects, the graph will grab the high function of those and display the graphs of all those months in order.

## Generating Fibonacci Lines

<img width="682" alt="image" src="https://github.com/paravsalaniwal/praopersonal/assets/111609656/75c376b7-7406-4cef-af5c-b20b2cc4c492">

This is inside the generategraph function which is drawing the Fibonacci lines at the corresponding decimal.