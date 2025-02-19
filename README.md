# Korean Maritime Vessel Infraction Matcher

## Overview
This project aims to match Korean maritime vessel infraction reports with suspected vessels to support research into fishing fleet activities. It addresses two key challenges:

1. The Korean Maritime Safety Tribunal website is in Korean
2. The site's search functionality is non-functional

The goal is to programmatically extract and match vessel names from infraction reports to create a searchable database linking vessels to their infractions.

## Background
This project builds on previous investigations into fishing fleet activities, particularly focused on Korean vessels. The source data includes:

- Korean Maritime Safety Tribunal website containing 860 infraction cases
- List of 60 Korean squid vessels of interest
- Each case includes vessel names and links to PDF reports (converted from .hwp format)

### Translation and Name Matching Challenges
- Vessel names appear in Korean (Hangul) on the KMST website but may be referenced in English in existing datasets
- Direct transliteration may vary (e.g., "명윤호" could be "Myung Yun Ho" or "Myeongyunho")
- Vessel names often include suffixes like "호" (ho) which means "vessel" in Korean
- Multiple vessels may share similar names with slight variations
- OCR and automatic translation tools may introduce inconsistencies

## Objective
Create a structured dataset matching vessel names to their infraction reports to enable researchers to:
- Easily find all infractions associated with specific vessels
- Access the original Korean PDF reports for manual translation and review
- Determine relevance of reports to ongoing research

## Implementation Approach

### Data Collection
1. Scrape the Korean Maritime Safety Tribunal website (https://www.kmst.go.kr/web/verdictList.do?menuIdx=121) to extract:
   - Case titles
   - Decision/report links 
   - Vessel names mentioned in titles
   - PDF reports (in .hwp format and renamed to English title extracted from the case title)
   - Vessel type classifications

### Data Processing
1. Scrape the KMST website to extract translated case titles and links to decision reports
2. Extract vessel names from case titles using pattern matching
3. Match extracted vessel names against the list of vessels of interest

