---
layout: page
title: Tempo Application
description: A modular C application for reading, validating, analyzing, and visualizing time series data. It supports interpolation, JSON input, and Gnuplot script generation.
img: assets/img/4.jpg
importance: 1
category: work
tools: C, Makefile, GitLab, Libtap, JSON, Gnuplot, Bats
related_publications: false
---
<div style="display: flex; justify-content: flex-end; margin-top: 1rem; margin-bottom: 1.5rem;">
  <a href="https://github.com/hocine-berranen/A-Modular-C-Tool-for-Time-Series-Analysis"
     target="_blank"
     rel="noopener"
     style="display: inline-flex; align-items: center; gap: 7px; background-color: #000; color: #fff !important; padding: 7px 12px; border-radius: 7px; text-decoration: none; font-weight: 700; font-size: 0.92rem; line-height: 1;">
    <svg height="17" width="17" viewBox="0 0 16 16" fill="white" aria-hidden="true" style="flex-shrink: 0;">
      <path d="M8 0C3.58 0 0 3.58 0 8a8 8 0 0 0 5.47 7.59c.4.07.55-.17.55-.38
      0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13
      -.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.5-1.07
      -1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12
      0 0 .67-.21 2.2.82a7.65 7.65 0 0 1 2-.27c.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82
      2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95
      .29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8 8 0 0 0 16 8
      c0-4.42-3.58-8-8-8Z"/>
    </svg>
    <span style="color: #fff !important; display: inline-block;">View Source</span>
  </a>
</div>

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Introduction
</div>

`tempo` is a command-line application written in C for reading, analyzing, and transforming time series data. It was built as a modular tool that can process chronological observations, validate their structure, compute useful statistics, interpolate intermediate values, and generate visualization-ready output.

The application supports multiple workflows, including formatted observation display, descriptive analysis, interpolation with configurable step sizes, JSON input parsing, and Gnuplot script generation. Its internal design is organized into separate modules for time series processing, datetime handling, validation, and command dispatching.

This project allowed me to work on several core software engineering topics, including low-level programming in C, dynamic memory management, modular architecture, input validation, testing, and the evolution of a codebase through multiple feature additions.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Problem / Context
</div>

Time series data is useful only when it can be read, validated, analyzed, and transformed reliably. A sequence of observations may look simple at first, but handling it properly requires structured parsing, chronological consistency, descriptive analysis, interpolation between known values, and sometimes export to visualization tools.

`tempo` was designed to address these needs through a command-line interface. The objective was to build a tool capable of turning raw time series input into useful outputs while keeping the code modular, maintainable, and easy to extend.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Main Features
</div>

`tempo` was designed as a small but flexible command-line tool centered around a few core features.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Descriptive analysis
</div>

The `describe` subcommand provides a quick summary of a time series by reporting its domain, codomain, size, duration, and amplitude. This makes it easy to inspect the overall structure of the data and understand its range in both time and value.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Observation display
</div>

The `show` subcommand prints all observations in chronological order using full timestamps. Instead of keeping the original offset-based format, it reconstructs complete datetimes, making the output easier to read and more useful for inspection.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Linear interpolation
</div>

The `interpolate` subcommand generates intermediate values between known observations. This allows the application to estimate missing values across time intervals and produce a denser representation of the series. The interpolation step can also be customized with different durations.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Multiple input formats
</div>

In addition to the original text format, the application supports JSON input. This makes the tool more flexible and closer to real-world data processing workflows, where structured formats are often required.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Visualization output
</div>

The `gnuplot` subcommand generates a valid Gnuplot script from the input time series. This makes it possible to move from raw data to graphical visualization without manually rewriting the data into another format.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Validation and error handling
</div>

The application validates subcommands, input formats, datetime values, observations, offsets, and options. It also reports clear error messages with appropriate exit codes, making the tool more reliable and predictable to use.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Technical Architecture
</div>

The project is organized around a modular C architecture, with each component responsible for a specific part of the application. This separation made the code easier to maintain, test, and extend as new features were added.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  <code>tempo.c</code>
</div>

This file acts as the entry point of the application. It parses command-line arguments, dispatches subcommands, handles options such as JSON input or interpolation step size, and connects the different modules together.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  <code>timeseries.c</code> / <code>timeseries.h</code>
</div>

This module contains the core logic of the project. It defines the main `Timeseries` structure and implements operations such as initialization, observation insertion, interpolation, statistics computation, formatted output, and Gnuplot script generation.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  <code>datetime.c</code> / <code>datetime.h</code>
</div>

This module handles datetime creation, validation, comparison, formatting, and time arithmetic. It is used throughout the project to convert offsets into full timestamps and to ensure chronological consistency.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  <code>validation.c</code> / <code>validation.h</code>
</div>

This part of the code centralizes validation and error reporting. It is responsible for detecting invalid subcommands, malformed input, invalid datetime values, incorrect options, and other error cases, while returning the appropriate exit codes.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Testing and build system
</div>

The project also includes a `Makefile`-based build system and a testing setup combining functional tests and unit tests. This helped ensure that new features could be added without breaking existing behavior.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Technical Challenges
</div>

Several parts of the project required more careful design than they might seem at first.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Managing a dynamic data structure
</div>

A time series may grow as new observations are read, which means the internal representation must be flexible. Implementing a dynamic structure with manual memory management in C required attention to allocation, resizing, insertion, and cleanup.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Designing interpolation behavior
</div>

Interpolation was one of the most algorithmic parts of the project. The application had to compute values between observations, preserve chronological accuracy, and support custom step durations while keeping the output clear and consistent.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Validating multiple input paths
</div>

Because the application supports both text and JSON input, validation had to cover several layers of the program. Handling malformed input, invalid datetime values, bad options, and incorrect offsets in a consistent way was an important part of making the application robust.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Input and Output Examples
</div>

One of the strengths of `tempo` is that it transforms raw time series input into several kinds of useful outputs depending on the selected subcommand.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Example of text input
</div>

The application can read a time series from standard input using a reference datetime followed by offset-value pairs.

<pre style="background-color: #aab8ca; padding: 18px 22px; border-radius: 4px; overflow-x: auto; margin-top: 1rem; margin-bottom: 1rem;"><code>2025-09-01T09:00:00
0 10
5 20
10 15</code></pre>

In this format, the first line defines the origin of the series, while each following line represents an observation with an offset in seconds and an associated integer value.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Example of descriptive output
</div>

Using the `describe` subcommand, the application reports key statistics about the series.

<pre style="background-color: #aab8ca; padding: 18px 22px; border-radius: 4px; overflow-x: auto; margin-top: 1rem; margin-bottom: 1rem;"><code>$ bin/tempo describe &lt; examples/6.ts
Domain: [2025-09-01T00:00:00, 2025-09-03T00:00:00]
Codomain: [10, 50]
Size: 6
Duration: 172800
Amplitude: 40</code></pre>

This output gives a compact overview of the temporal range and value range of the series.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Example of interpolation
</div>

Using the `interpolate` subcommand, the application generates intermediate values between known observations.

<pre style="background-color: #aab8ca; padding: 18px 22px; border-radius: 4px; overflow-x: auto; margin-top: 1rem; margin-bottom: 1rem;"><code>$ bin/tempo interpolate &lt; examples/3_10s.ts
2025-09-01T09:00:00 10
2025-09-01T09:00:01 12
2025-09-01T09:00:02 14
2025-09-01T09:00:03 16
2025-09-01T09:00:04 18
2025-09-01T09:00:05 20
2025-09-01T09:00:06 19
2025-09-01T09:00:07 18
2025-09-01T09:00:08 17
2025-09-01T09:00:09 16
2025-09-01T09:00:10 15</code></pre>

This makes the tool capable of producing a denser and more continuous representation of the original series.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Example of JSON input
</div>

The application also accepts JSON input for structured data ingestion.

<pre style="background-color: #aab8ca; padding: 18px 22px; border-radius: 4px; overflow-x: auto; margin-top: 1rem; margin-bottom: 1rem;"><code>{
  "origin": "2025-09-01T00:00:00",
  "observations": [
    { "offset": 0, "value": 10 },
    { "offset": 28800, "value": 40 },
    { "offset": 57600, "value": 15 }
  ]
}</code></pre>

This format makes the application easier to integrate with other tools and workflows that already rely on structured data formats.

<div style="font-size: 1.6rem; font-weight: 500; margin-top: 1.5rem; margin-bottom: 0.5rem;">
  Example of visualization output
</div>

With the `gnuplot` subcommand, the application generates a valid Gnuplot script from the input time series. This makes it possible to turn raw observations into a visual representation without manually rewriting the data.

Rather than displaying the full script on the page, I would present this feature with a short explanation and, ideally, a screenshot of the generated graph.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Tools and Technologies
</div>

This project combines low-level programming, structured data handling, automated testing, and command-line tooling. The main technologies used are:

- C for the core application logic
- Make / Makefile for compilation and task automation
- Git for version control and feature-based development
- JSON / Jansson for structured input parsing
- Gnuplot for visualization script generation
- Bats for functional testing
- Libtap for unit testing

These tools made it possible to build a project that is both technical and practical, combining algorithmic logic, validation, testing, and modular software organization.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  What I Learned
</div>

Working on `tempo` helped me strengthen several important software engineering skills.

First, I became much more comfortable with modular programming in C, especially when organizing a project across multiple source files with clearly separated responsibilities. I also improved my understanding of dynamic memory management, including allocation, reallocation, and cleanup in a context where mistakes can easily lead to instability.

The project also gave me practical experience with input validation and error handling. Making the application behave consistently across multiple commands, options, and input formats required careful design and attention to edge cases.

Finally, I learned the importance of maintaining and extending an evolving codebase. As new features were introduced, I had to think not only about making them work, but also about preserving clarity, avoiding regressions, and keeping the project structure maintainable.

<div style="background-color: #2f4358; color: white; font-size: 2rem; font-weight: 700; padding: 4px 14px; margin-top: 2rem; margin-bottom: 1.2rem;">
  Final Result
</div>

`tempo` evolved into a complete command-line tool for working with time series data. It can read structured observations, validate multiple input formats, compute descriptive statistics, interpolate values, and generate visualization-ready output through Gnuplot scripts.

Beyond the final features themselves, the project reflects a broader approach to software development: building a tool incrementally, organizing it into clear modules, extending it without losing structure, and supporting it with validation and testing. For me, it became a strong practical exercise in writing reliable C code and shaping a small but real technical system from the ground up.

<div style="display: flex; justify-content: flex-end; margin-top: 1rem; margin-bottom: 1.5rem;">
  <a href="https://github.com/hocine-berranen/A-Modular-C-Tool-for-Time-Series-Analysis"
     target="_blank"
     rel="noopener"
     style="display: inline-flex; align-items: center; gap: 7px; background-color: #000; color: #fff !important; padding: 7px 12px; border-radius: 7px; text-decoration: none; font-weight: 700; font-size: 0.92rem; line-height: 1;">
    <svg height="17" width="17" viewBox="0 0 16 16" fill="white" aria-hidden="true" style="flex-shrink: 0;">
      <path d="M8 0C3.58 0 0 3.58 0 8a8 8 0 0 0 5.47 7.59c.4.07.55-.17.55-.38
      0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13
      -.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.5-1.07
      -1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12
      0 0 .67-.21 2.2.82a7.65 7.65 0 0 1 2-.27c.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82
      2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95
      .29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8 8 0 0 0 16 8
      c0-4.42-3.58-8-8-8Z"/>
    </svg>
    <span style="color: #fff !important; display: inline-block;">View Source</span>
  </a>
</div>
