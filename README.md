[README.md](https://github.com/user-attachments/files/23749069/README.md)
# Film Production Embezzlement Dataset Tools

This repository contains:
- `template.csv` — CSV template/schema for documenting film-production embezzlement/finance-fraud cases.
- `sample_cases.csv` — A small set of verified example rows (Sadleir, Van Eman, McConley, Julio Caro) plus one synthetic row for training.
- `harvest_dojo.py` — A starter script to fetch DOJ press releases (or other URLs) and extract amounts/titles. Edit `doj_urls.txt` to add more URLs to harvest.
- `doj_urls.txt` — starter list of DOJ/SEC press release URLs used to create the sample rows.
- `requirements.txt` — Python deps to run the harvester.

## How to use locally
1. Clone this repo on your machine.
2. Create a virtualenv and install requirements:
   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
3. Edit `doj_urls.txt` to add any DOJ press release URLs you want to harvest (one per line).
4. Run the harvester:
   ```bash
   python harvest_dojo.py --urls doj_urls.txt --out harvested_cases.csv
   ```
5. The script will create `harvested_cases.csv` with a simple parsed output. Use the template to map fields into your canonical dataset.

## Notes & next steps
- The harvester is intentionally simple. DOJ pages vary in structure — for robust harvesting, add site-specific parsing rules or use the DOJ sitemap/API if available.
- Always verify amounts, defendants, and outcomes against court dockets (PACER) and primary documents before publishing.
- To push to GitHub: `git init`, add files, commit, create a repo, and push. Or upload via the GitHub UI.

## Sources used for sample rows
- William Sadleir — DOJ press release & SEC (May 22, 2020). See: https://www.justice.gov/usao-sdny/pr/former-chairman-and-ceo-movie-production-company-arrested-fraud-charges and https://www.sec.gov/newsroom/press-releases/2020-122
- Jason Van Eman — DOJ (July 22, 2022) sentencing press release: https://www.justice.gov/usao-sdfl/pr/movie-producer-sentenced-over-21-years-role-film-financing-scheme
- Benjamin McConley — DOJ plea (Oct 25, 2019): https://www.justice.gov/usao-sdfl/pr/film-producer-pleads-guilty-movie-financing-fraud-scheme
- Julio Caro — DOJ (Nov 8, 2016) sentencing: https://www.justice.gov/usao-cdca/pr/independent-producer-sentenced-18-months-prison-stealing-money-generated-film-should

Last generated: 2025-11-17 UTC
