# quoteoftheday

1. Build a command line application which when executed, returns a different quotation per day.

Hints: You can use the following API https://quotes.rest/qod (pass headers: { 'Accept': 'application/json' } to get JSON response

Example: 

C:\Users\akD>./qod

Output

“You’re off to great places, today is your day. Your mountain is waiting, so get on your way.”

2. (Optional) Build an app then fetches quote of the day and displays it to the user.

const axios = require('axios')
const chalk = require('chalk');

const url = "https://quotes.rest/qod"

// make a get request to the url
axios({
  method: 'get',
  url: url,
  headers: { 'Accept': 'application/json' }, // this api needs this header set for the request
}).then(res => {
  const quote = res.data.contents.quotes[0].quote
  const author = res.data.contents.quotes[0].author
  const log = chalk.green(`${quote} - ${author}`) // we use chalk to set the color green on successful response
  console.log(log)
}).catch(err => {
  const log = chalk.red(err) // we set the color red here for errors.
  console.log(log)
})

in cmnd window: chmod +x qod
