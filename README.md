# Finnhub-ts

Why? There is an existing one [finnhub-js](https://github.com/Finnhub-Stock-API/finnhub-js)

> Because it's not working in every enviroment

## Source

Swagger file:
[swagger.json](https://finnhub.io/static/swagger.json)

OpenAPI Client:
[openapi-generator-cli.jar](https://github.com/OpenAPITools/openapi-generator)

How generate new version:

1. `java -jar .\openapi-generator-cli.jar generate -i .\swagger.json -o .\ -g typescript-axios --skip-validate-spec -c .\openapi-generator.json`
2. update npm version
3. push to npm

## finnhub-ts@1.0.0

This generator creates TypeScript/JavaScript client that utilizes [axios](https://github.com/axios/axios). The generated Node module can be used in the following environments:

Environment

- Node.js
- Webpack
- Browserify

Language level

- ES5 - you must have a Promises/A+ library installed
- ES6

Module system

- CommonJS
- ES6 module system

It can be used in both TypeScript and JavaScript. In TypeScript, the definition should be automatically resolved via `package.json`. ([Reference](http://www.typescriptlang.org/docs/handbook/typings-for-npm-packages.html))

## Usage for 3rd party apps:

```typescript
import { DefaultApi } from 'finnhub-ts'
const finnhubClient = new DefaultApi({
  apiKey: 'YOUR-API-KEY',
  isJsonMime: (input) => {
    try {
      JSON.parse(input)
      return true
    } catch (error) {}
    return false
  },
})
```

### For React.js visit my other repo

TODO add link

### Usage with [Axios interceptors](https://axios-http.com/docs/interceptors)

```typescript
finnhubClient.axios.interceptors.response.use(
  (response) => response,
  (error) => {
    switch (error.code) {
      case 'ERR_BAD_REQUEST':
        // API limit for example (30 calls/second)
        console.log(error.response.data.error)
        break

      default:
        console.log('error: ', error)
    }
  }
)
```

### Example Usage

```typescript
companyEarnings('AAPL').then((res) => {
  console.log(res.data)
})
```

Output:

```json
[
  {
    "actual": 2.56,
    "estimate": 2.38,
    "period": "2019-03-31",
    "symbol": "AAPL"
  },
  {
    "actual": 4.21,
    "estimate": 4.15,
    "period": "2018-12-31",
    "symbol": "AAPL"
  },
  {
    "actual": 2.88,
    "estimate": 2.75,
    "period": "2018-09-30",
    "symbol": "AAPL"
  },
  {
    "actual": 2.32,
    "estimate": 2.11,
    "period": "2018-06-30",
    "symbol": "AAPL"
  }
]
```

### All functions

Official [Docs](https://finnhub.io/docs/api/) and API info

```typescript
const {
  aggregateIndicator,
  bondPrice,
  bondProfile,
  companyBasicFinancials,
  companyEarnings,
  companyEarningsQualityScore,
  companyEbitEstimates,
  companyEbitdaEstimates,
  companyEpsEstimates,
  companyEsgScore,
  companyExecutive,
  companyNews,
  companyPeers,
  companyProfile,
  companyProfile2,
  companyRevenueEstimates,
  country,
  covid19,
  cryptoCandles,
  cryptoExchanges,
  cryptoProfile,
  cryptoSymbols,
  earningsCalendar,
  economicCalendar,
  economicCode,
  economicData,
  etfsCountryExposure,
  etfsHoldings,
  etfsProfile,
  etfsSectorExposure,
  fdaCommitteeMeetingCalendar,
  filings,
  filingsSentiment,
  financials,
  financialsReported,
  forexCandles,
  forexExchanges,
  forexRates,
  forexSymbols,
  fundOwnership,
  indicesConstituents,
  indicesHistoricalConstituents,
  insiderSentiment,
  insiderTransactions,
  internationalFilings,
  investmentThemes,
  ipoCalendar,
  marketNews,
  mutualFundCountryExposure,
  mutualFundHoldings,
  mutualFundProfile,
  mutualFundSectorExposure,
  newsSentiment,
  ownership,
  patternRecognition,
  pressReleases,
  priceTarget,
  quote,
  recommendationTrends,
  revenueBreakdown,
  similarityIndex,
  socialSentiment,
  stockBasicDividends,
  stockBidask,
  stockCandles,
  stockDividends,
  stockLobbying,
  stockNbbo,
  stockSplits,
  stockSymbols,
  stockTick,
  stockUsaSpending,
  stockUsptoPatent,
  stockVisaApplication,
  supplyChainRelationships,
  supportResistance,
  symbolSearch,
  technicalIndicator,
  transcripts,
  transcriptsList,
  upgradeDowngrade,
} = finnhubClient
```

## Developing:
