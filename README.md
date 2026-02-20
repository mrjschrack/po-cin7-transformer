# PO Transformer Tool

A standalone browser-based tool that converts retail purchase orders from various vendor formats into Cin7-ready import files. Built to streamline warehouse operations by eliminating manual data entry.

## Features

- Automatic vendor format recognition via fingerprinting
- Smart company name matching using Cin7 contact exports
- Company name alias system for handling vendor-specific naming inconsistencies
- Delivery instruction templates with dynamic placeholders
- Internal comments templates
- Batch processing of multiple POs into a single Cin7 import file
- Save, edit, and delete custom format configurations

## Supported Vendors

- Scheels
- Academy Sports
- Zoro
- Tractor Supply Drop Ship

## Usage

Open `po-transformer.html` in any modern browser. No installation or server required.

1. (Optional) Load a Cin7 contact export for smart company matching
2. Drag and drop one or more PO files onto the tool
3. Map columns if prompted for an unrecognized format
4. Export the Cin7-ready CSV