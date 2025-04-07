3MG Excel Processing Pipeline-
Mission:

This repository contains the Azure Data Factory pipeline infrastructure for processing complex Excel files with multiple sheets, irregular structures, and non-tabular content. Our mission is to automate the extraction and transformation of data from various Excel sources into standardized outputs, eliminating manual processing errors and reducing processing time.
Excel Complexity Challenges

Our Excel files present several unique challenges:
Multi-sheet files: Each Excel file contains multiple sheets with different data structures
Non-tabular content: Sheets contain comments, notes, and other non-tabular data interspersed with actual tables
Irregular formatting: Table positions vary, headers appear at different row positions
Inconsistent naming: Sheet names and column headers may vary across files
Data validation requirements: Only certain data patterns are valid for processing
Mixed data types: Numerical data sometimes formatted as text, dates in various formats
Pipeline Architecture
The pipeline implements a sophisticated approach:
Dynamic sheet detection: An Azure Function uses EPPlus to analyze Excel files and identify all sheets
Two-level processing:
Parent pipeline (Excel_MultiSheet_Advanced_Pipeline) finds Excel files and extracts sheet metadata
Child pipeline (Process_Excel_Sheets_Pipeline_advanced) processes each sheet with appropriate rules
Validation & Filtering:
Files are verified for accessibility before processing
Non-tabular content is filtered using pattern recognition
Row density analysis identifies valid data regions
Error handling: Failed processing is captured with detailed diagnostics
Parameterization: Fully parameterized for flexible deployment
Code-Driven Approach
This repository enables an infrastructure-as-code approach:
ARM templates: All pipeline components defined as ARM templates
Version control: Full history of pipeline changes
CI/CD integration: Modifications can be deployed through CI/CD pipelines
Code review: Changes can be reviewed before deployment
Rollback capability: Easy rollback to previous versions if needed
Deployment Workflow
Development:
Clone the repository
Modify ARM templates with new pipeline logic
Test in development environment
Deployment:
Push changes to the repository
CI/CD pipeline automatically deploys to test environment
After validation, promote to production
Monitoring:
Pipeline runs are logged in Azure Monitor
Failed files are routed to error containers with diagnostics
Email notifications for execution summaries
This architecture ensures reliable processing of complex Excel files while maintaining flexibility to handle new file formats through code-based configuration rather than manual UI adjustments.
