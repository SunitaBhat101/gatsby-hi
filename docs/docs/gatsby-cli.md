---
title: Commands (Gatsby CLI)
tableOfContentsDepth: 2
---

एक Gatsby एप्लिकेशन को सुरु करने और चलने के लिए और डेवलपमेंट सर्वर चलाना और गैट्सबी एप्लीकेशन डिप्लॉयमेंट के लिए बनाना जैसे फंक्शनैलिटीज का इस्तेमाल करने के लिए Gatsby कमांड लाइन टूल (सीएलआई) एक मुख्य प्रवेश बिंदु है।

_हम [रीडमी](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-cli/README.md) में gatsby-सीएलआई के जैसा डॉक्यूमेंटेशन देते हैं और हमारी [चीट शीट](/docs/cheat-sheet/) में सारी टॉप कमांड्स रहती है जो प्रिंट आउट के लिए तैयार है।_

## gatsby-cli का उपयोग कैसे करें

Gatsby सीएलआई (`gatsby-cli`) को एक्ज़ीक्यूटेबल के रूप में पैक किया जाता है जिसका ग्लोबली इस्तेमाल किया जा सकता है। Gatsby सीएलआई [npm](https://www.npmjs.com/) के माध्यम से उपलब्ध है और इसे स्थानीय स्तर पर उपयोग करने के लिए `npm install -g gatsby-cli` चलाकर ग्लोबली इनस्टॉल किया जाना चाहिए।

पूरी मदद के लिए  `gatsby --help` चलाएँ।

आप इन कमांड्स के `package.json` स्क्रिप्ट वैरिएंट्स का भी उपयोग कर सकते हैं, आमतौर पर ये _आपके लिए_ ज़्यादातर [starters](/docs/starters/) डॉक्स के साथ एक्सपोज्ड रहता है। उदाहरण के लिए, यदि आप अपने एप्लीकेशन में [`gatsby develop`](#develop) कमांड उपलब्ध कराना चाहते हैं, तो` package.json` खोलें और एक स्क्रिप्ट डालें:

```json:title=package.json
{
  "scripts": {
    "develop": "gatsby develop"
  }
}
```

## API कमांड्स

### `new`

```
gatsby new [<site-name> [<starter-url>]]
```

#### तर्क

| तर्क    | विवरण                                                                                                                                                                                                     |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
site-name   | आपके Gatsby साइट का नाम, जिसका उपयोग प्रोजेक्ट डायरेक्टरी बनाने के लिए भी किया जाता है। |
| starter-url | एक Gatsby स्टार्टर URL या लोकल फाइल पाथ। डिफ़ॉल्ट रूप से [Gatsby-starter-default](https://github.com/gatsbyjs/gatsby-starter-default) और अधिक जानकारी के लिए [Gatsby starters](/docs/gatsby-starters/) डॉक्स को देखें। |

> ध्यान दें: The `site-name` केवल अक्षरों और संख्याओं से मिलकर बना होना चाहिए। यदि आप नाम में एक `.`, `./` या `<space>` निर्दिष्ट करते हैं, तो `gatsby new` एरर दिखायेगा।

#### उदाहरण

डिफॉल्ट स्टार्टर का उपयोग करके `my-awesome-site` नाम से एक Gatsby साइट बनाएँ:

```shell
gatsby new my-awesome-site
```

- [Gatsby स्टार्टर ब्लॉग](https://www.gatsbyjs.org/starters/gatsbyjs/gatsby-starter-blog/) का उपयोग करके, `my-awesome-blog-site` नामक एक Gatsby साइट बनाएँ:

```shell
gatsby new my-awesome-blog-site https://github.com/gatsbyjs/gatsby-starter-blog
```

 यदि आप दोनों आर्ग्युमेंट्स को छोड़ देते हैं, तो सीएलआई इन इनपुट्स को मांगने लिए एक इंटरैक्टिव शेल चलाएगा:

```shell
gatsby new
? What is your project called? › my-gatsby-project
? What starter would you like to use? › - Use arrow-keys. Return to submit.
❯  gatsby-starter-default
   gatsby-starter-hello-world
   gatsby-starter-blog
   (Use a different starter)
```

अधिक विवरण के लिए [Gatsby स्टार्टर डॉक्स](https://www.gatsbyjs.org/docs/gatsby-starters/) देखें।

### `develop`

एक बार जब आप एक Gatsby साइट इनस्टॉल कर लेते हैं, तो अपनी प्रॉजेक्ट की रूट फोल्डर मे जाएँ और डेवेलपमेंट सर्वर शुरू करें:

`gatsby develop`

#### ओप्शंस

|     ओप्शंस      | विवरण                                     |
| :-------------: | ----------------------------------------------- |
| `-H`, `--host`  | होस्ट सेट करें। इसकी डिफ़ॉल्ट वैल्यू localhost है                |
| `-p`, `--port`  | पोर्ट सेट करें। इसकी डिफ़ॉल्ट वैल्यू 8000 है                      |
| `-o`, `--open`  | आपके लिए अपने (डिफ़ॉल्ट) ब्राउज़र में साइट खोलता है            |
| `-S`, `--https` | HTTPS का उपयोग करें                                      |


Gatsby का उपयोग करके आप HTTPS डेवलपमेंट सर्वर कैसे सेट कर सकते हैं, यह जानने के लिए [लोकल HTTPS गाइड](/docs/local-https/) का उपयोग करें।

#### अन्य उपकरणों पर प्रीव्यू परिवर्तन

आप एक ही नेटवर्क पर अन्य उपकरणों पर अपने dev एन्वाइरन्मेंट की जानकारी के लिए होस्ट ओप्शंस के साथ Gatsby develop कमांड का उपयोग कर सकते हैं, निचे दी गयी कमांड चलाएं:

```shell
Gatsby develop -H 0.0.0.0
```

तब टर्मिनल सामान्य रूप से जानकारी लॉग करेगा, लेकिन इसके अतिरिक्त एक URL भी शामिल होगी जिसे आप एक ही नेटवर्क पर किसी और क्लाइंट से नेविगेट करके देख सकते है की साइट कैसे रेंडर हो रही है।

```
अब आप ब्राउज़र में gatsbyjs.org देख सकते हैं।
⠀
  लोकल:          http://0.0.0.0:8000/
  अपने नेटवर्क पर:  http://192.168.0.212:8000/ // हाइलाइट-लाइन
```

**ध्यान दें**: आप Windows पर 0.0.0.0:8000 पर नहीं जा सकते हैं (लेकिन Windows पर localhost:8000 या "आपके नेटवर्क की" URL से सब कुछ चलेगा)

### `build`

Gatsby साइट की रूट डाइरेक्टरी में एप्लीकेशन कंपाइल करे और डेप्लाय्मेंट की त्यारी करे:

`gatsby build`

#### ओप्शंस

|            ओप्शंस            | विवरण                                                                                               |
| :--------------------------: | --------------------------------------------------------------------------------------------------------- |
|       `--prefix-paths`       | लिंक प्रीफिक्सड पाथस के साथ साइट बनाएं (pathPrefix को अपनी कॉन्फिग में डालें)                                       |
|        `--no-uglify`         | JS bundles को अगलीफाई किये बिना साइट बनाएं (डिबगिंग के लिए)                                                  |
| `--open-tracing-config-file` | ट्रेसर कॉन्फ़िगरेशन फ़ाइल (OpenTracing कम्पेटिबल)। [प्रदर्शन अनुरेखण](/docs/performance-tracing/) देखें|
| `--no-color`, `--no-colors`  | टर्मिनल के कलर्ड आउटपुट को डिसएबल करता है                                                                       |

इन बिल्ड ओप्शंस के अलावा, अधिक अड्वान्स कॉन्फ़िगरेशन के लिए कुछ ऑप्शनल [बिल्ड एन्वाइरन्मेंट वेरियबल्स](/docs/environment-variables/#build-variables) हैं जो एडजस्ट कर सकते हैं की बिल्ड कैसे रन हो। उदाहरण के लिए, एन्वाइरन्मेंट वेरियबल के रूप में `CI = true` को सेट करने से वो [डंब टर्मिनल्स] (https://en.wikipedia.org/wiki/Computer_terminal#Dumb_terminals) के लिए स्ट्रक्चर्ड आउटपुट बनाएगा।

### `serve`

अपनी साइट को टेस्ट करने के लिए, प्रोडक्शन बिल्ड को एक Gatsby साइट के रुट में सर्व करें::

`gatsby serve`

#### ओप्शंस

|      ओप्शंस      | विवरण                                                                              |
| :--------------: | ---------------------------------------------------------------------------------------- |
| `-H`, `--host` | होस्ट सेट करें। इसकी डिफ़ॉल्ट वैल्यू localhost है               |
| `-p`, `--port`  | पोर्ट सेट करें। इसकी डिफ़ॉल्ट वैल्यू 9000 है                    |
| `-o`, `--open`  | आपके लिए अपने (डिफ़ॉल्ट) ब्राउज़र में साइट खोलता है           |
| `--prefix-paths` | लिंक प्रीफिक्सड पाथस के साथ साइट को सर्व करें (अगर आपकी gatsby-config में pathPrefix के साथ साइट बनी है) |

### `info`

एक Gatsby साइट की रुट में, एन्वाइरन्मेंट की उपयोगी जानकारी प्राप्त करें जो बग की रिपोर्ट करते समय आवश्यक होगी:

`gatsby info`

#### ओप्शंस

|       ओप्शंस        | विवरण                                             |
| :-----------------: | ------------------------------------------------------- |
| `-C`, `--clipboard` | क्लिपबोर्ड पर एन्वाइरन्मेंट की जानकारी को ऑटोमैजिकली रूप से कॉपी करें |

### `clean`

एक Gatsby साइट के रुट में से cache (.cache फोल्डर) और पब्लिक डायरेक्ट्रीज को पूरी तरह से मिटा दें:

`gatsby clean`

यह अंतिम उपाय के रूप में उपयोगी है जब आपके लोकल प्रोजेक्ट में इश्यू हो या कॉंटेंट रिफ्रेश न हो। इससे जो इश्यूज़ ठीक हो सकते हैं उनमें से कुछ हैं:

- स्टेल डेटा, उदाहरण के लिए यह file/resource/etc. दिखाई नहीं दे रहा है।
- GraphQL एरर, उदाहरण के लिए यह GraphQL रीसोर्स मौजूद होना चाहिए लेकिन ये मौजूद नहीं है।
- डिपेंडेन्सी इश्यूस, उदाहरण के लिए इनवैलिड वर्शन, कंसोल में गुप्त एरर आदि।
- प्लगिन इश्यूस, उदाहरण के लिए एक लोकल प्लगइन डेवेलप करना और उसके कुछ भी बदलाव प्रॉजेक्ट मे दिखाई ना देना।

### `plugin`

Gatsby plugin से संबंधित कमांड चलाएँ।

#### `docs`

`gatsby plugin docs`

प्लगइन का उपयोग करने और बनाने के बारे में आपको दस्तावेज़ों को निर्देशित करता है।

### Repl

अपने Gatsby एन्वाइरन्मेंट के संदर्भ में एक Node.js REPL (इंटरेक्टिव शेल) प्राप्त करें:

`gatsby repl`

Gatsby आपको कमांड्स टाइप करने और एक्सप्लोर करने के लिए प्रोमपट करेगा। जब वो यह दिखाता है: `gatsby >`

एक कमांड में टाइप कर सकते हैं, जैसे कि इनमें से एक:

`babelrc`

`components`

`dataPaths`

`getNodes()`

`nodes`

`pages`

`schema`

`siteConfig`

`staticQueries`

[GraphQL explorer](/docs/introducing-graphiql/) के साथ उपयोग करने पर, ये REPL कमांड्स आपके Gatsby साइट के डेटा को समझने के लिए बहुत सहायक हो सकते हैं।

अधिक जानकारी के लिए, [Gatsby REPL डॉक्युमेंटेशन](/docs/gatsby-repl/) देखें।

### कलर आउटपुट को डिसेबल करना

सीएलआई ओप्शंस `--no-color` के अलावा एन्वाइरन्मेंट वेरियबल `NO_COLOR` की उपस्थिति का सम्मान करता है ([no-color.org](https://no-color.org/) देखें।)

## अपने अगले प्रोजेक्ट के लिए अपने डिफ़ॉल्ट पैकेज मैनेजर को कैसे बदलें?

जब आप पहली बार एक नया प्रोजेक्ट बनाने के लिए `gatsby new` का उपयोग करते हैं, तो आपको yarn और npm के बीच अपने डिफ़ॉल्ट पैकेज मैनेजर को चुनने के लिए कहा जाता है।

```shell
Which package manager would you like to use ? › - Use arrow-keys. Return to submit.
❯  yarn
   npm
```

एक बार जब आप अपनी पसंद बना लेते हैं, तो सीएलआई किसी भी बाद के प्रोजेक्ट के लिए आपकी प्राथमिकता के लिए नहीं पूछेगा।

यदि आप इसे अपने अगले प्रोजेक्ट के लिए बदलना चाहते हैं, तो आपको सीएलआई द्वारा स्वचालित रूप से बनाई गई कॉन्फ़िग फ़ाइल को एडिट करना होगा।
यह फ़ाइल आपके सिस्टम पर उपलब्ध है: `~/.config/gatsby/config.json`

इसमें आपको कुछ इस तरह से दिखने वाला है।

```json:title=config.json
{
  "cli": {
    "packageManager": "yarn"
  }
}
```

अपने `packageManager` की वैल्यू को एडिट करें, सेव करें और `gatsby new` को इस्तेमाल करके आप अपना अगला प्रोजेक्ट बनाने के लिए तैयार हैं।
