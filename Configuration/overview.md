# Overview

## Config Files

An administrator pre-defines one or more GeoReports config files, each defining how a single PDF Report will be constructed.

A single config file contains all the logic required to produce a PDF Report on almost any subject matter.

The configuration file is an XML based configuration file to allow administrator configuration and has a file extension of .config (rather than .xml) as this is a protected file extension in the servlet.

Each config file comprises the following major sections

- **Settings** – All settings related to producing the final output
- **Pages** – A sequential listing of all page definitions required