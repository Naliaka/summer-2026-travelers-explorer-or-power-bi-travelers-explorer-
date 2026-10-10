# ✈️ Summer 2026 Travellers Explorer | Power BI Dashboard

An interactive Business Intelligence project exploring European holiday costs, comparing pricing components, and helping travellers evaluate budget-friendly holiday options using Power BI and DAX.

**Project status:** In progress — Page 1 completed.

---

## 📊 Dashboard Preview

<img width="1527" height="858" alt="image" src="https://github.com/user-attachments/assets/7539abda-b9fa-4d88-bf09-7fc939c411fe" />


## 🗺️ Project Roadmap

- **Page 1 — Travellers Explorer:** Interactive holiday-cost exploration, destination mapping, cost comparisons, and budget-friendly deals.
- **Page 2 — Weather & Fit:** Planned exploration of weather conditions and destination suitability.
- **Page 3 — Best Value:** Planned comparison of holiday options by value.

## 🌟 Key Features — Page 1

- **Dynamic Top 10 Deal Ranking:** Uses custom DAX ranking logic with `RANKX` to identify lower-cost holiday options within the selected filter context.
- **Geographic Cost Mapping:** Visualises average holiday costs across destinations, including France, Italy, Spain, and Portugal, where represented in the report.
- **Cost Component Analysis:** Breaks down major holiday expenses, including flights, accommodation, local transport, food, attractions, and tourist taxes.
- **Interactive Filtering:** Supports exploration by origin city, traveller type, accommodation type, and duration.

## 🛠️ Data Model & DAX Logic

### Top 10 Deal Ranking Measure

```dax
Top 10 Filter_ =
VAR RowRank =
    RANKX(
        ALLSELECTED(Top_Deals_Summary),
        CALCULATE(
            SUM(Top_Deals_Summary[Avg Cost Per Person])
        ),
        ,
        ASC,
        DENSE
    )
RETURN
    IF(RowRank <= 10, 1, 0)
```

This measure ranks deal-summary rows by cost in ascending order and returns `1` for rows ranked within the first 10 positions. Apply it as a visual-level filter, setting the value to `1`.

**Implementation note:** Dense ranking can return more than 10 rows when multiple deals share a rank. Verify the result against the actual visual before describing it as exactly 10 deals.

## 💻 Tools & Technologies

- Microsoft Power BI
- DAX
- Data modelling and interactive visualisation
- ZoomCharts custom visuals

## 🏅 Acknowledgements & Credits

Special thanks to ZoomCharts for hosting [Power BI Challenge 20](https://zoomcharts.com/en/microsoft-power-bi-custom-visuals/challenges/), which inspired the report's design and analytical approach.

**Focus:** Travel analytics, interactive visual storytelling, and user-centred dashboard design.

