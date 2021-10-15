# Dates

Edlink uses [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) formatted dates in its API. They look like this:

```
2021-07-05T14:48:00.000Z
```

The format is as follows:

```
YYYY-MM-DDThh:mm:ss.sssZ
```

`YYYY` represents the year, `MM` represents the month, and `DD` represents the day. `T` is a literal separator between the date and time-- it's always present, and it's always just the letter T. `hh` represents the hour, `mm` represents the minute, and `ss.sss` represents the second. `Z` indicates that the timezone used will be UTC.

Most languages have a built-in facility to create dates in this format. If you are using JavaScript or TypeScript, you can convert a `Date` to this format using [`Date.prototype.toISOString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString).

> Edlink will take care of any timezone conversions when communicating with LMS or SIS systems. As such, it's generally preferred that you send dates to the Edlink API in UTC.