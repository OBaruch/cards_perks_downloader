# cards_perks_downloader

**cards_perks_downloader** is a Python library designed to download and centralize information on the perks offered by credit card issuers and banks worldwide. The tool extracts data directly from official websites (for example, American Express, Visa, MasterCard, and local banks) and consolidates it into a standardized format to facilitate consultation and analysis.

## Features

- **Modular Connectors:**  
  Each data source is integrated through modules or "plugins" that adhere to a standard interface. This allows contributors from different countries to add specific connectors for their local institutions.
  
- **Real-Time Data:**  
  The library is designed to extract the most up-to-date information directly from official websites, ensuring that the benefits shown are as current as possible.
  
- **Simple Interface and Extensible API:**  
  It offers straightforward functions for integrating data extraction into other applications, as well as a CLI to facilitate downloading from the terminal.

## Installation

The library can be installed using pip:

```bash
pip install cards_perks_downloader
