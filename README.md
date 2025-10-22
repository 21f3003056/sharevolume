# SEC Company Common Stock Shares Outstanding Viewer

This project provides a single-page responsive web application to display the maximum and minimum common stock shares outstanding for a given company, fetched directly from the SEC EDGAR API. The application is built with a focus on a clean, responsive user interface using Tailwind CSS and dynamic data fetching with vanilla JavaScript.

## Features

-   Displays company name and its maximum and minimum common stock shares outstanding values, along with the corresponding fiscal years.
-   Fetches data for Aon plc (CIK 0000315293) by default.
-   Supports dynamic CIK lookup: append `?CIK=YOUR_CIK_NUMBER` to the URL to fetch data for any 10-digit CIK.
-   Responsive design for various screen sizes.
-   Utilizes a proxy (AllOrigins) for cross-origin requests when fetching data for dynamic CIKs.

## Setup and Usage

This is a single-file application. To run it:

1.  Save the `index.html` content to a file named `index.html`.
2.  Open `index.html` in any modern web browser.

### Default View

Upon opening `index.html` without any parameters, it will display data for **Aon plc**:

```
index.html
```

### Dynamic CIK Lookup

To view data for a different company, append the CIK (Central Index Key) as a query parameter to the URL. For example, to view data for Apple Inc. (CIK 0000320193):

```
index.html?CIK=0000320193
```

Replace `0000320193` with the 10-digit CIK of the company you wish to inspect.

## Data Source

Data is sourced from the U.S. Securities and Exchange Commission (SEC) EDGAR API:
`https://data.sec.gov/api/xbrl/companyconcept/CIKXXXXXXXXXX/dei/EntityCommonStockSharesOutstanding.json`

A descriptive `User-Agent` header is used for all SEC API requests as per SEC guidance. When fetching dynamic CIKs, `api.allorigins.win` is used as a proxy to circumvent CORS restrictions.

## Development Notes

-   The application filters common stock shares outstanding data to include only fiscal years (`fy`) greater than "2020" with valid numeric values.
-   The `index.html` file is self-contained with inline CSS (Tailwind CDN) and JavaScript.

## License

This project is licensed under the MIT License. See the `LICENSE` file for full details.
