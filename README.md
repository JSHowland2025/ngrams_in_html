#N-Gram Word Cloud - Phase 3 User Sentiment Version
README

Overview

This is a browser-based n-gram word cloud tool. It runs locally in a web browser and does not require Streamlit, Python, NLTK, an API key, or an internet connection after the HTML file is saved.

The app lets you upload a CSV file, choose a text column, generate 1-word, 2-word, or 3-word n-grams, view a frequency table, color the word cloud using palette or sentiment logic, and export the results as PNG or CSV files.

Because processing happens locally in the browser, uploaded CSV data is not sent to a server by this app.

Main Features

1. CSV upload
   - Upload a CSV file directly in the browser.
   - The first row should contain column headers.
   - The app automatically lists available columns after upload.

2. N-gram generation
   - Supports 1-word, 2-word, and 3-word n-grams.
   - Lets you choose the text column to analyze.
   - Lets you set the minimum frequency.
   - Lets you set the maximum number of displayed n-grams.

3. Stopword handling
   - Includes a default English stopword list.
   - Allows custom stopwords entered as comma-separated or space-separated terms.

4. Color palettes
   - Includes generic palette options such as viridis-like, plasma-like, cividis-like, and Set2-like palettes.
   - Includes two JEA palette options:

     JEA_blues:
       JEA Brand Blue: #012169
       JEA_blue_1:    #1D4F91
       JEA_blue_2:    #3ba5d4
       JEA_blue_3:    #4EC3E0

     JEA_new:
       New_1: #004990
       New_2: #898990
       New_3: #00DEFF
       New_4: #004FFF
       New_5: #001C36

5. Sentiment coloring
   - Palette-based coloring is available for standard word cloud output.
   - Sentiment coloring can be enabled using either:
     a. Estimated sentiment from the text, or
     b. A user-selected numeric score column from the uploaded CSV.

6. User-defined sentiment from CSV
   - Select a numeric score column from the uploaded CSV.
   - If scores already appear to be in a -1 to 1 range with negative values, the app uses them directly.
   - Otherwise, scores are automatically normalized to a -1 to 1 scale.
   - Missing or non-numeric values are filled using the column mean before normalization.

7. Sentiment threshold slider
   - The neutral threshold controls how wide the grey/neutral band is around zero.
   - Lower threshold values make words turn negative or positive colors more quickly.
   - Higher threshold values keep more words grey unless sentiment is stronger.
   - The threshold applies to all sentiment palettes.

8. Exports
   - Download standard PNG word cloud.
   - Download high-resolution PNG word cloud.
   - Download displayed n-gram frequency table as CSV.
   - Download all matching n-grams as CSV.
   - Copy the displayed table to the clipboard.

How to Run

1. Save the file named ngram_wordcloud_phase3_user_sentiment.html to your computer.
2. Open the file in a modern web browser such as Chrome, Edge, Firefox, or Safari.
3. Upload a CSV file.
4. Select the text column to analyze.
5. Adjust the n-gram and color settings.
6. Click Generate word cloud.

Recommended CSV Format

The CSV should have a header row and at least one text column.

Example:

Comment,Satisfaction,SurveyDate
"The service was fast and helpful",5,2026-05-01
"My bill was confusing",2,2026-05-02
"The representative solved my issue",5,2026-05-03

For user-defined sentiment, include a numeric score column. The score column may be on any scale, such as 1-5, 0-10, 0-100, or -1 to 1. The app will normalize most numeric scales automatically.

Typical Workflow

1. Upload the CSV.
2. Choose the main comment or response text column.
3. Select n-gram size:
   - 1 word for individual terms.
   - 2 words for common phrases.
   - 3 words for longer recurring phrases.
4. Set minimum frequency to remove rare phrases.
5. Add custom stopwords if needed.
6. Choose a color method:
   - Standard palette for frequency-based word clouds.
   - Sentiment coloring for positive/neutral/negative visualization.
7. If using user-defined sentiment, choose the numeric score column.
8. Adjust the neutral threshold slider until the balance of grey versus colored words looks appropriate.
9. Export the word cloud and/or CSV table.

Notes on Sentiment

Text-estimated sentiment uses a lightweight embedded browser-side lexicon. It is designed to keep the app local and dependency-free. It is not identical to VADER or other Python sentiment tools.

User-defined sentiment from a CSV score column is often preferable when the dataset already contains satisfaction, rating, NPS, survey score, or other structured sentiment information.

The sentiment color assigned to an n-gram is based on the average sentiment score of the rows where that n-gram appears.

Limitations

1. This version does not include date filtering.
2. This version does not include mask image support.
3. This version does not include PDF or SVG export.
4. This version does not include lemmatization.
5. Very large CSV files may be slower because all processing occurs in the browser.
6. The built-in CSV parser handles common CSV files, including quoted fields, but highly irregular files may need cleanup first.

Troubleshooting

Problem: The file uploads, but the wrong text column is selected.
Solution: Manually choose the intended text column from the dropdown.

Problem: The word cloud has too many unhelpful terms.
Solution: Add those terms to the custom stopwords box and regenerate.

Problem: No n-grams appear.
Solution: Lower the minimum frequency, increase the maximum number of n-grams, or verify that the selected text column contains usable text.

Problem: Sentiment colors look too strong.
Solution: Increase the neutral threshold slider.

Problem: Sentiment colors look too grey.
Solution: Decrease the neutral threshold slider.

Problem: The CSV score column is not available for user-defined sentiment.
Solution: Confirm that the column contains numeric values. Remove symbols or non-numeric text if needed.

Privacy and Data Handling

This app processes the uploaded CSV locally in the browser. It does not include any API calls and does not upload the CSV contents to a remote service.

Version Notes

This version builds on the earlier browser implementation by adding sentiment coloring, user-selected sentiment score columns, and a neutral threshold slider while simplifying the color palette section to a smaller set of generic and JEA palettes.
