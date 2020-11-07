# App Store Version Information Changer

## Getting started

### Step1

- Match the versionInformations to the AppStore localized languages with the same order
- Run in browser console

```javascript
const versionInformations = [
  "Bug fixes and performance improvements", // "English (U.S.)Primary
  "Bug fixes and performance improvements", // Arabic
  "Bug fixes and performance improvements", // Catalan
  "Bug fixes and performance improvements", // Chinese (Simplified)
  "Bug fixes and performance improvements", // Chinese (Traditional)
  "Bug fixes and performance improvements", // Croatian
  "Bug fixes and performance improvements", // Czech
  "Bug fixes and performance improvements", // Danish
  "Bug fixes and performance improvements", // Dutch
  "Bug fixes and performance improvements", // English (Australia)
  "Bug fixes and performance improvements", // English (Canada)
  "Bug fixes and performance improvements", // English (U.K.)
  "Bug fixes and performance improvements", // Finnish
  "Bug fixes and performance improvements", // French
  "Bug fixes and performance improvements", // French (Canada)
  "Bug fixes and performance improvements", // German
  "Bug fixes and performance improvements", // Greek
  "Bug fixes and performance improvements", // Hebrew
  "Bug fixes and performance improvements", // Hindi
  "Bug fixes and performance improvements", // Hungarian
  "Bug fixes and performance improvements", // Indonesian
  "Bug fixes and performance improvements", // Italian
  "Bug fixes and performance improvements", // Japanese
  "Bug fixes and performance improvements", // Korean
  "Bug fixes and performance improvements", // Malay
  "Bug fixes and performance improvements", // Norwegian
  "Bug fixes and performance improvements", // Polish
  "Bug fixes and performance improvements", // Portuguese (Brazil)
  "Bug fixes and performance improvements", // Portuguese (Portugal)
  "Bug fixes and performance improvements", // Romanian
  "Bug fixes and performance improvements", // Russian
  "Bug fixes and performance improvements", // Slovak
  "Bug fixes and performance improvements", // Spanish (Mexico)
  "Bug fixes and performance improvements", // Spanish (Spain)
  "Bug fixes and performance improvements", // Swedish
  "Bug fixes and performance improvements", // Thai
  "Hata düzeltmeleri ve performans iyileştirmeleri", // Turkish
  "Bug fixes and performance improvements", // Ukrainian
  "Bug fixes and performance improvements", // Vietnamese
];
```

### Step2

- Run in browser console

```javascript
const delay=2e3,onInputEvent=new Event("input"),localizationOptionMenu=document.querySelectorAll("div.tb-popover > div")[1],localizationOptions=localizationOptionMenu.getElementsByTagName("ul")[0].children,changeLocale=(e,n)=>new Promise((t,o)=>{const a=e.getElementsByTagName("button")[0];a?(a.click(),console.info(`changeLocale::localization button clicked || buttonVal: ${a.textContent}, index: ${n}`),setTimeout(()=>t(),2e3)):o(`changeLocale::Button not found || index: ${n}`)}),changeValue=(e,n)=>new Promise((e,t)=>{const o=versionInformations[n];o?(document.querySelector("#whatsNew").value=o,document.querySelector("#whatsNew").dispatchEvent(onInputEvent),console.info(`changeValue::whatsNew input changed || newVal: ${o}, index: ${n}`),setTimeout(()=>e(),2e3)):t(`changeValue::Version information not found || index: ${n}`)}),start=async e=>{const n=localizationOptions[e];if(n)try{await changeLocale(n,e),await changeValue(0,e)}catch(e){console.error(e)}finally{start(e+1)}else console.info("done")};start(0);
```

## Uncompressed Code

```javascript
const versionInformations = [
  "Bug fixes and performance improvements", // "English (U.S.)Primary
  "Bug fixes and performance improvements", // Arabic
  "Bug fixes and performance improvements", // Catalan
  "Bug fixes and performance improvements", // Chinese (Simplified)
  "Bug fixes and performance improvements", // Chinese (Traditional)
  "Bug fixes and performance improvements", // Croatian
  "Bug fixes and performance improvements", // Czech
  "Bug fixes and performance improvements", // Danish
  "Bug fixes and performance improvements", // Dutch
  "Bug fixes and performance improvements", // English (Australia)
  "Bug fixes and performance improvements", // English (Canada)
  "Bug fixes and performance improvements", // English (U.K.)
  "Bug fixes and performance improvements", // Finnish
  "Bug fixes and performance improvements", // French
  "Bug fixes and performance improvements", // French (Canada)
  "Bug fixes and performance improvements", // German
  "Bug fixes and performance improvements", // Greek
  "Bug fixes and performance improvements", // Hebrew
  "Bug fixes and performance improvements", // Hindi
  "Bug fixes and performance improvements", // Hungarian
  "Bug fixes and performance improvements", // Indonesian
  "Bug fixes and performance improvements", // Italian
  "Bug fixes and performance improvements", // Japanese
  "Bug fixes and performance improvements", // Korean
  "Bug fixes and performance improvements", // Malay
  "Bug fixes and performance improvements", // Norwegian
  "Bug fixes and performance improvements", // Polish
  "Bug fixes and performance improvements", // Portuguese (Brazil)
  "Bug fixes and performance improvements", // Portuguese (Portugal)
  "Bug fixes and performance improvements", // Romanian
  "Bug fixes and performance improvements", // Russian
  "Bug fixes and performance improvements", // Slovak
  "Bug fixes and performance improvements", // Spanish (Mexico)
  "Bug fixes and performance improvements", // Spanish (Spain)
  "Bug fixes and performance improvements", // Swedish
  "Bug fixes and performance improvements", // Thai
  "Hata düzeltmeleri ve performans iyileştirmeleri", // Turkish
  "Bug fixes and performance improvements", // Ukrainian
  "Bug fixes and performance improvements", // Vietnamese
];

const delay = 2000;
const onInputEvent = new Event("input");
const localizationOptionMenu = document.querySelectorAll("div.tb-popover > div")[1];
const localizationOptions = localizationOptionMenu.getElementsByTagName("ul")[0].children;

const changeLocale = (localizationOption, index) => {
  return new Promise((resolve, reject) => {
    const button = localizationOption.getElementsByTagName("button")[0];

    if (!button) {
      reject(`changeLocale::Button not found || index: ${index}`);
      return;
    }

    button.click();

    console.info(`changeLocale::localization button clicked || buttonVal: ${button.textContent}, index: ${index}`);
    setTimeout(() => resolve(), delay);
  });
};

const changeValue = (localizationOption, index) => {
  return new Promise((resolve, reject) => {
    const versionInformation = versionInformations[index];

    if (!versionInformation) {
      reject(`changeValue::Version information not found || index: ${index}`);
      return;
    }

    document.querySelector("#whatsNew").value = versionInformation;
    document.querySelector("#whatsNew").dispatchEvent(onInputEvent);

    console.info(`changeValue::whatsNew input changed || newVal: ${versionInformation}, index: ${index}`);
    setTimeout(() => resolve(), delay);
  });
};

const start = async (index) => {
  const localizationOption = localizationOptions[index];

  if (!localizationOption) {
    console.info("done");
    return;
  }

  try {
    await changeLocale(localizationOption, index);
    await changeValue(localizationOption, index);
  } catch (e) {
    console.error(e);
  } finally {
    start(index + 1);
  }
};

start(0);
```
