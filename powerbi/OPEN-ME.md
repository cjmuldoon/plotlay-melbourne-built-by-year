# Opening the Power BI report

`MelbourneBuiltByYear.pbip` is a Power BI Project: the report (`MelbourneBuiltByYear.Report`, PBIR format) and the semantic model (`MelbourneBuiltByYear.SemanticModel`, TMDL) saved as text, so the repo can show every change. Power BI Desktop opens it like a `.pbix`.

## What you need

- Power BI Desktop for Windows, a recent version (2026). Projects and the PBIR report format are standard in current versions. If Desktop is older than about mid 2025, turn on **File, Options and settings, Options, Preview features, Power BI Project (.pbip) save option** and **Store reports using enhanced metadata format (PBIR)**, then restart Desktop.
- The repo folder on the Windows machine. In Parallels the Mac home folder is usually shared as `\\Mac\Home`.

## Open it

1. In Windows, go to the repo's `powerbi` folder and double-click `MelbourneBuiltByYear.pbip`, or in Desktop use **File, Open report, Browse reports** with the file type set to *Power BI project files (\*.pbip)*.
2. The visuals are empty the first time. Select **Refresh** on the Home ribbon.
   - By default the data is read from the repo's public copy on GitHub (`DataFolder` is `https://raw.githubusercontent.com/cjmuldoon/plotlay-melbourne-built-by-year/main/data/`). If Desktop asks how to connect, choose **Anonymous** and then **Connect**.
   - To read the files from disk instead, go to **Home, Transform data, Edit parameters** and set `DataFolder` to the full path of the repo's `data` folder, **ending with a backslash** (for example `\\Mac\Home\plotlay-melbourne-built-by-year\data\`). Then select **OK** and **Apply changes**.
   - If Desktop warns about privacy levels, choose **Ignore privacy levels** (all the sources are public open data).
3. Check the numbers (below).

If the report was updated while open, close Power BI and reopen the .pbip rather than using Apply external changes.

## Check the numbers after Refresh

After **Refresh**, the cards on **By decade** read:

| Card | Should read |
|---|---|
| Buildings standing, CBD | 1,548 |
| With a construction year | 1,320 |
| Share with no year | 14.7% |

The column chart peaks in the 1920s (189 buildings). On **Eras**, the last era (1991 to 2024) has 184 buildings and 48.3% of the floor space estimate; the eras before 1946 together have 18.4%.

## The model

- **Buildings**: one row per structure in the CBD (`data/tables/buildings.csv`): the year built from the CLUE record in it (blank where none), floors, height, how it was matched, address and use. Measures: `Buildings standing`, `Dated buildings`, `No year share`, `Median height m`.
- **Decades** and **Eras**: buildings standing today by the decade or era they were built, with a floor space estimate (each footprint part's area times its height over 3.5 m a floor, to compare only). Measures: `Buildings built`, `Floor space estimate m2`, `Era buildings`, `Era floor space m2`, `Era floor share`.

## The map

**Where** is an Azure Maps visual: each building at its centre, sized by its height. If Azure Maps is off, turn it on in **File, Options and settings, Options, Security** (Use Azure Maps visual).

## Save a .pbix too

After the refresh, use **File, Save as** with the type **Power BI file (\*.pbix)** to save `powerbi\MelbourneBuiltByYear.pbix`. It includes the data, so it opens without a refresh.

## Publish (only if you choose to)

Use **Home, Publish**. In the Power BI service, set the semantic model's **Data source credentials** for the GitHub address to **Anonymous**. Scheduled refresh then works with no gateway. **Publish to web** makes a public link, so only use it if you mean the report to be public.

## Shot list for the website and the video

| # | Shot | How | Length |
|---|---|---|---|
| 1 | The rule by state | As it opens | still |
| 2 | Closures since 2005 | As it opens | still |
| 3 | The drive | As it opens; hover a block group in Pittsburg County | still |
| 4 | Counties | As it opens | still |
| 5 | Beds | As it opens | still |

Save page images into `powerbi/Screenshots/` (a PDF export of all pages is fine too).
