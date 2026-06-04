# AI Resume Screener

## The Problem

Recruiters spend entire days manually reading resumes to fill a single role. The process is slow, inconsistent, and biased — by resume 200, no human is making good decisions. Small and mid-size companies face this the most because they lack budget for enterprise ATS tools like Workday or Greenhouse.

## The Solution

A lightweight Python tool that automates the first pass of resume screening using Claude (Anthropic API).

The recruiter inputs a job description. The tool reads every PDF resume in a folder, scores each one against the job description, and returns a ranked shortlist with scores, strengths, gaps, and a one-line summary per candidate — in under 10 seconds per resume.

No manual reading. No inconsistency. Recruiters only spend time on the top candidates.

## How It Works

1. Paste a job description
2. Upload candidate resumes as PDFs
3. The tool extracts text from each resume using PyMuPDF
4. Each resume is sent to Claude with a structured scoring prompt
5. Claude returns a JSON score across four dimensions: overall fit, skills match, experience match, and a plain-language recommendation
6. Results are ranked and exported to a two-sheet Excel file ready to share

## Features

- Screen many candidates against one job — ranked shortlist output
- Screen one candidate against many roles — best role match output
- Bias detection report flagging gender, age, nationality, ethnicity, disability, and socioeconomic indicators
- Excel export for all three outputs

## Tech Stack

- Python
- Anthropic API (Claude)
- PyMuPDF — PDF text extraction
- Pandas + OpenPyXL — Excel export
- Google Colab — development environment

## Results

Tested on a Data Analyst job description requiring Python, SQL, Excel, and data visualization experience. The tool correctly identified skill gaps and experience mismatches within seconds, producing a ranked output a recruiter could act on immediately.

The bias detection module flagged age disclosure, gender inference from name, nationality indicators, and socioeconomic signals — all common sources of unconscious bias in manual screening.

## Who This Is For

- Startups and SMEs doing high-volume hiring without an ATS
- Staffing agencies screening large applicant pools
- University career offices managing student job applications

## Setup

1. Clone the repository
2. Open the notebook in Google Colab
3. Add your Anthropic API key to Colab Secrets as ANTHROPIC_API_KEY
4. Upload PDF resumes to the /content/resumes folder
5. Run all cells in order

## Next Steps

- Add a simple web UI so recruiters without coding knowledge can use it
- Support bias-blind screening mode that strips flagged fields before scoring
