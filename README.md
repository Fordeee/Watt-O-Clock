# Watt O'Clock

A small web app that finds the greenest time to run household appliances in Great Britain.

Enter a postcode and the app reads the next 24 hours of the regional carbon intensity forecast for your area. For each appliance (dishwasher, washing machine, tumble dryer, oven, EV charge, immersion heater) you can set the run time, and it recommends the start time that puts the appliance's heaviest power draw on the cleanest electricity.

## How it works

- Forecast data comes live from the NESO Carbon Intensity API (`api.carbonintensity.org.uk`), half-hourly, by postcode region.
- Each appliance has a consumption profile: a fixed heating burst at the start, an optional burst at the end (such as a dishwasher's hot rinse), and a low-power middle that stretches with the run time you choose.
- The app scores every possible start time by the energy-weighted carbon intensity the appliance would actually see, and picks the lowest.

The whole app is a single file, `index.html`, with no build step or server.

## Limitations

- Forecasts are indicative and are revised every 30 minutes, so recommendations can change between refreshes, especially for times many hours ahead.
- Appliance profiles and energy figures are typical values. Your own machine will differ; the energy figure can be edited in the app.
- Great Britain only. Northern Ireland is on a separate grid.

## Data licence

Carbon intensity data: [NESO Carbon Intensity API](https://carbonintensity.org.uk), licensed under CC BY 4.0.
