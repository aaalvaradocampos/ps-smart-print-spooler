# 🖨️ PowerShell Paired Batch Printer

A robust PowerShell script built to handle complex physical printing workflows. This tool automatically pairs documents from two different directories (e.g., a primary Word document and a supporting PDF receipt), sorts them using advanced logic (alphabetical and Regex numbering), and sends them to the printer sequentially. 

It is designed with hardware limits in mind, utilizing controlled pauses (`Start-Sleep`) to prevent print spooler crashes, and includes batching logic to skip previously printed files and print in specific chunks.

## ✨ Features

- **📄 Cross-Format Pairing:** Simultaneously handles `.doc/.docx` files from one folder and `.pdf` files from another, ensuring they print back-to-back.
- **🧠 Smart Sorting (Regex):** Uses Regular Expressions to extract numbers from filenames, allowing correct numerical sorting (preventing "File 10" from printing before "File 2").
- **⏸️ Spooler Protection:** Injects precise delays between print commands to allow the physical printer's memory to process the jobs without freezing.
- **⏭️ Custom Batching & Resuming:** Easily configure the script to skip a specific number of documents (useful if a paper jam occurred) and print the next batch of `X` files.

## 🚀 Setup & Usage

1. Open **Windows PowerShell ISE** or your preferred code editor.
2. Copy the script code and paste it into a new file.
3. Update the Configuration variables at the top of the script:
   - `$carpetaPrincipal`: The path to the folder containing your Word documents.
   - `$carpetaComprobantes`: The path to the folder containing your PDF files.
   - `$skipCount`: How many file pairs you want to skip (Set to `0` to start from the beginning).
   - `$printLimit`: How many file pairs to print in this execution batch.
4. Save the file as `PairedPrinter.ps1`.
5. Right-click the file and select **Run with PowerShell**, or execute it directly from the console.

## ⚠️ Important Notes

- **Default Printer & Applications:** The script sends the files to the default Windows printer. Ensure Word and your default PDF reader are configured properly, as the script invokes their native print verbs.
- **Equal File Counts:** The script assumes there is a 1:1 relationship between the files in the Word folder and the files in the PDF folder.
