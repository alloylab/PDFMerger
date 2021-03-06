# PDFMerger
Simple wrapper for merging pdfs for PHP >= 7.2 based on setasign/fpdi and fpdf libraries.

When using a symfony framework you can use [tomsgu/pdf-merger-bundle](https://github.com/Tomsgu/PDFMergerBundle) bundle.
# Installation
```bash
composer require tomsgu/pdf-merger
```

# Usage
```php
$pdfCollection = new PdfCollection();
$pdfCollection->addPdf('filename.pdf', PdfFile::ALL_PAGES, PdfFile::ORIENTATION_PORTRAIT);
$pdfCollection->addPdf('filename2.pdf', '1-4,9', PdfFile::ORIENTATION_LANDSCAPE);
$pdfCollection->addPdf('filename3.pdf');

$fpdi = new Fpdi();
$merger = new PdfMerger($fpdi);
/**
 * Available modes: MODE_FILE, MODE_DOWNLOAD, MODE_STRING, MODE_BROWSER
 * Orientation: This is a fallback if the orientation wasn't specified when adding pdf.
 */
$merger->merge($pdfCollection, 'output.pdf', PdfMerger::MODE_FILE, PdfFile::ORIENTATION_LANDSCAPE);
```
