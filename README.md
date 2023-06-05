# Set-Map-and-Higher-order-function
### 1.Use reduce to concatenate all the countries and to produce this sentence: Estonia,Finland, Sweden, Denmark, Norway, and IceLand are north European countries
```js
const countries = ['Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland'];

const sentence = countries.reduce((accumulator, country, index) => {
  if (index === 0) {
    return country;
  } else if (index === countries.length - 1) {
    return accumulator + ', and ' + country;
  } else {
    return accumulator + ', ' + country;
  }
}, '');

console.log(`${sentence} are north European countries.`);

```
### 2.Use find to find the first country containing only six letters in the countries array
```js
const country = countries.find((country) => country.length === 6);
console.log(country);

```
### 3.Find out which letter is used many times as initial for a country name from the countries array (eg. Finland, Fiji, France etc
```js
const initials = {};
countries.forEach((country) => {
  const initial = country[0];
  if (initial in initials) {
    initials[initial]++;
  } else {
    initials[initial] = 1;
  }
});

let maxCount = 0;
let mostUsedInitial;

for (const initial in initials) {
  if (initials[initial] > maxCount) {
    maxCount = initials[initial];
    mostUsedInitial = initial;
  }
}

console.log(`The letter '${mostUsedInitial}' is used many times as the initial for a country name.`);

```

### 4.Use the countries information, in the data folder. Sort countries by name, by capital, by population
```js
const countriesData = [
  { name: 'Finland', capital: 'Helsinki', population: 5591217 },
  { name: 'Sweden', capital: 'Stockholm', population: 10380422 },
  { name: 'Denmark', capital: 'Copenhagen', population: 5814461 },
  { name: 'Norway', capital: 'Oslo', population: 5388604 },
  { name: 'Iceland', capital: 'Reykjavik', population: 356991 }
];

// Sort by name
const sortedByName = countriesData.sort((a, b) => a.name.localeCompare(b.name));
console.log(sortedByName);

// Sort by capital
const sortedByCapital = countriesData.sort((a, b) => a.capital.localeCompare(b.capital));
console.log(sortedByCapital);

// Sort by population
const sortedByPopulation = countriesData.sort((a, b) => b.population - a.population);
console.log(sortedByPopulation);

```
### 5.Find the 10 most spoken languages:
```js
const mostSpokenLanguages = (countries, count) => {
  const languages = {};

  countries.forEach((country) => {
    const countryLanguages = country.languages;
    countryLanguages.forEach((language) => {
      if (language in languages) {
        languages[language]++;
      } else {
        languages[language] = 1;
      }
    });
  });

  const sortedLanguages = Object.entries(languages).sort((a, b) => b[1] - a[1]);
  return sortedLanguages.slice(0, count).map(([language, count]) => ({ language, count }));
};

console.log(mostSpokenLanguages(countries, 10));
console.log(mostSpokenLanguages(countries, 3));

```

### 6.const a = [4, 5, 8, 9]
###   const b = [3, 4, 5, 7]
###      1. Find a union b
###      2. Find a intersection b
###      3. Find a with b
```js
const a = [4, 5, 8, 9];
const b = [3, 4, 5, 7];

// Union
const union = [...new Set([...a, ...b])];
console.log(union);

// Intersection
const intersection = a.filter((value) => b.includes(value));
console.log(intersection);

// Difference (a with b)
const difference = a.filter((value) => !b.includes(value));
console.log(difference);

```

### 7.Use the countries data to find the 10 most spoken languages
```js
const countriesData = [
  { name: 'Finland', languages: ['Finnish', 'Swedish'] },
  { name: 'Sweden', languages: ['Swedish'] },
  { name: 'Denmark', languages: ['Danish'] },
  { name: 'Norway', languages: ['Norwegian'] },
  { name: 'Iceland', languages: ['Icelandic'] }
];

const mostSpokenLanguages = (countries, count) => {
  const languages = {};

  countries.forEach((country) => {
    const countryLanguages = country.languages;
    countryLanguages.forEach((language) => {
      if (language in languages) {
        languages[language]++;
      } else {
        languages[language] = 1;
      }
    });
  });

  const sortedLanguages = Object.entries(languages).sort((a, b) => b[1] - a[1]);
  return sortedLanguages.slice(0, count).map(([language, count]) => ({ [language]: count }));
};

console.log(mostSpokenLanguages(countriesData, 10));
console.log(mostSpokenLanguages(countriesData, 3));

```
