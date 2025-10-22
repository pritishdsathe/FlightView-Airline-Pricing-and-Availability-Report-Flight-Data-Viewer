# FlightView: Airline Pricing and Availability Report – Flight Data Viewer

## Overview

The **FlightView: Airline Pricing and Availability Report** is an SAP ABAP report designed for displaying flight-related data from the SFLIGHT table. The report allows users to filter and view details of flights based on parameters like airline carrier, flight dates, and currencies. It also provides interactive user features, such as dynamic selection of currency, help documentation for specific fields, and custom error handling.

## Purpose

This report is intended for airline business users or operational staff who need to view flight details filtered by specific criteria. The purpose of this tool is to present flight data clearly, enabling users to analyze pricing, availability, and flight details based on various parameters.

## Key Features

### 1. Dynamic Selection Screen
- **Carrier ID (p_carrid):** Specify the airline (carrier) ID.
- **Flight Date Range (s_fldate):** Default range from January 24, 2019, to the current date, with an option to modify.
- **Currency (s_curr):** Filter results by currency with an F4 help for predefined options (USD, EUR, JPY).
- **Checkbox (p_chk1):** Activates/deactivates the currency field depending on the selection.

### 2. Interactive Currency Selection with F4 Help
- **F4 Help Dialog:** Uses the `F4IF_INT_TABLE_VALUE_REQUEST` function to show available currencies (USD, EUR, JPY).
- **Error Handling:** If an invalid currency is entered, the user is prompted to select a valid option.

### 3. Flight Data Retrieval
- **Data Query:** A `SELECT` query pulls relevant data from the SFLIGHT table based on the user’s filters:
  - Carrier ID (carrid)
  - Flight Date (fldate)
  - Currency (currency)
- **Key Data Retrieved:** Flight price (price), plane type (planetype), connection ID (connid).

### 4. Display of Flight Information
- **Classical List Format:** Data is displayed in a clean, readable table with headers like Carrier ID, Connection ID, Flight Date, Price, Currency, and Plane Type.
- **Pagination:** Users can navigate large datasets across multiple pages, with page numbers shown at both top and bottom.

### 5. Help Documentation (F1 Help)
- **F1 Help for Currency Field:** Displays custom documentation for the currency field (`ZDOCCUR`), providing context about available currencies.

### 6. Conditional Field Activation Based on Checkbox
- **Dynamic Activation:** The checkbox (p_chk1) controls whether the currency field (s_curr) is active or not, using screen modification techniques.

### 7. Error Handling and Validation
- **Currency Validation:** Ensures only valid currencies (USD, EUR, JPY) are selected, displaying an error message if not.
- **Help Object Retrieval:** Notifies the user if the custom help object (`ZDOCCUR`) is missing.
- **Data Retrieval:** Includes error handling for when no records are returned from the `SELECT` query.

### 8. Report Layout and Structure
- **Structured Output:**
  - Page Header: Includes static text (e.g., TEXT-001) and the current page number.
  - Data Table: Flight information displayed in aligned columns.
  - Page Footer: Displays pagination and custom footer text (TEXT-008).
- **Formatting:** A clean format using line separators for better readability.

### 9. End of Selection & Footer Messages
- **Footer Messages:** Includes end-of-selection messages and line separators for visual clarity.

## Technical Details

- **Data Selection (Database Access):** 
  - Uses a `SELECT` statement on the SFLIGHT table with filters for Carrier ID, Flight Date, and Currency.
  - Supports filtering by date range (s_fldate) and specific currencies.

- **F4 Help Functionality:**
  - The currency field (`s_curr`) uses the `F4IF_INT_TABLE_VALUE_REQUEST` function to present predefined options from an internal table (USD, EUR, JPY).

- **Dynamic Screen Modification:**
  - Dynamically shows or hides the currency field based on the checkbox state using the SCREEN table.

- **Error Handling:**
  - Handles errors with custom messages for invalid input, missing help objects, or empty query results.

## Usage Scenario

### Business Use Cases:
1. **Scenario 1: Operations Manager**
   - Review flight prices for a specific carrier over the past month, filtered by USD and EUR currencies.
2. **Scenario 2: Financial Analyst**
   - Extract and report flight prices in JPY for a specific airline over a defined period.

### End-User Interaction:
- Users interact with the selection screen to specify the **Carrier ID**, **Flight Date Range**, and **Currency**.
- Once data is filtered, it is displayed in a paginated list format, with the option to scroll through results.
- F1 help is available for the currency field, and error messages are displayed for invalid inputs.

## Future Enhancements

- **Extended Currency Options:** Dynamically populate currency options from a master data table to simplify future updates.
- **Export Functionality:** Add functionality to export flight data to Excel or CSV for further analysis.
- **Performance Optimization:** Implement database-level pagination for better performance with large datasets.

## Setup and Installation

### Prerequisites:
- SAP System with ABAP access.
- Access to the **SFLIGHT** table and **ZDOCCUR** help object.

### Installation:
1. Copy the ABAP report code into your SAP system.
2. Ensure that the `SFLIGHT` table is accessible.
3. Implement the `F4IF_INT_TABLE_VALUE_REQUEST` function for currency selection.
4. Customize the report layout and text constants (TEXT-001, TEXT-002, etc.) as needed.

### Usage:
1. Run the report in your SAP GUI.
2. Use the selection screen to filter by **Carrier ID**, **Flight Date Range**, and **Currency**.
3. View the results in a paginated list.
4. Access F1 Help for additional information about the currency field.

---

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

---

## Contributing

Feel free to fork the repository and submit pull requests. If you'd like to contribute, please ensure that any code follows the coding standards and that proper testing is done.

---

## Acknowledgements

- Thanks to the SAP community for sharing helpful resources and guidelines on ABAP report development.

