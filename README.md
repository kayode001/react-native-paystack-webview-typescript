# React-Native-Paystack-WebView typescript

<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->

[![All Contributors](https://img.shields.io/badge/all_contributors-7-orange.svg?style=flat-square)](#contributors-)

<!-- ALL-CONTRIBUTORS-BADGE:END -->

The package allows you accept payment using paystack and guess what , it doesn't require any form of linking, just install and begin to use .

### [](https://github.com/just1and0/React-Native-Paystack-WebView#installation)Installation

Add React-Native-Paystack-WebView to your project by running;

`npm install react-native-paystack-webview`

or

`yarn add react-native-paystack-webview`

### **One more thing**

To frontload the installation work, let's also install and configure dependencies used by this project, being **react-native-webview**

run

`yarn add react-native-webview`

for IOS: `cd iOS && pod install && cd ..`

for expo applications run;

`expo install react-native-webview`

and that's it, you're all good to go!

### [](https://github.com/just1and0/React-Native-Paystack-WebView#usage)Usage

```javascript
import PaystackWebView from "react-native-paystack-webview";
import React, { Component } from "react";
import { View } from "react-native";

class MyApp extends Component {
  render() {
    return (
      <View style={{ flex: 1 }}>
        <PaystackWebView
          buttonText="Pay Now"
          showPayButton={false}
          paystackKey="your-public-key-here"
          amount={120000}
          billingEmail="paystackwebview@something.com"
          billingMobile="09787377462"
          billingName="Oluwatobi Shokunbi"
          ActivityIndicatorColor="green"
          SafeAreaViewContainer={{ marginTop: 5 }}
          SafeAreaViewContainerModal={{ marginTop: 5 }}
          onCancel={(e) => {
            // handle response here
          }}
          onSuccess={(e) => {
            // handle response here
          }}
          autoStart={false}
        />
      </View>
    );
  }
}
```

### Usage 2

```javascript
import PaystackWebView from 'react-native-paystack-webview';
import React, {Component} from 'react';
import {View} from 'react-native';

class MyApp extends Component {
  render() {
    return (
      <View style={{flex: 1}}>
        <PaystackWebView
          buttonText="Pay Now"
          showPayButton={false}
          paystackKey="your-public-key-here"
          amount={120000}
          billingEmail="paystackwebview@something.com"
          billingMobile="09787377462"
          billingName="Oluwatobi Shokunbi"
          ActivityIndicatorColor="green"
          SafeAreaViewContainer={{marginTop: 5}}
          SafeAreaViewContainerModal={{marginTop: 5}}
          handleWebViewMessage={(e) => {
            // handle the message
          }}
          onCancel={(e) => {
            // handle response here
          }}
          onSuccess={(e) => {
            // handle response here
          }}
          autoStart={false}
          refNumber={uuid()} // this is only for cases where you have a reference number generated
          renderButton=((onPress) => {
            <Button onPress={onPress}>
              Pay Now
            <Button>
          })
        />
      </View>
    );
  }
}
```

## Use ref's

make use of ref's to start transaction. See example below;

```javascript import PaystackWebView from 'react-native-paystack-webview';
import React, {useRef} from 'react';
import {View, TouchableOpacity,Text} from 'react-native';
function Pay(){
   const childRef = useRef();

  return(
    <View style={{flex: 1}}>
        <PaystackWebView
          showPayButton={false}
          paystackKey="your-public-key-here"
          amount={120000}
          billingEmail="paystackwebview@something.com"
          billingMobile="09787377462"
          billingName="Oluwatobi Shokunbi"
          ActivityIndicatorColor="green"
          SafeAreaViewContainer={{marginTop: 5}}
          SafeAreaViewContainerModal={{marginTop: 5}}
          onCancel={(e) => {  // handle response here }}
          onSuccess={(e) => {  // handle response here }}
           ref={childRef}
        />

            <TouchableOpacity onPress={()=> childRef.current.StartTransaction()}>
             <Text>pay now</Text>
						<TouchableOpacity/>
      </View>
)
}
```

## Note:

You can also make use of the new props `autoStart` to initiate payment once the screen mounts. Just see `autoStart={true}`. This is set to `false` by default.

## API's

#### [](https://github.com/just1and0/object-to-array-convert#all-object-to-array-convert-props)all React-Native-Paystack-WebView API

| Name                                 |                                                                                           use/description                                                                                           |                                                      extra |
| :----------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | ---------------------------------------------------------: |
| `buttonText`                         |                                                                                     Defines text on the button                                                                                      |                                         default: `Pay Now` |
| `textStyles`                         |                                                                                  Defines styles for text in button                                                                                  |                                                     `nill` |
| `btnStyles`                          |                                                                                      Defines style for button                                                                                       |                                                     `nill` |
| `paystackKey`                        |                                                                   Public or Private paystack key(visit paystack.com to get yours)                                                                   |                                                     `nill` |
| `amount`                             |                                                                                          Amount to be paid                                                                                          |                                                     `nill` |
| `ActivityIndicatorColor`             |                                                                                           color of loader                                                                                           |                                           default: `green` |
| `billingEmail(required by paystack)` |                                                                                            Billers email                                                                                            |                                            default: `nill` |
| `billingMobile`                      |                                                                                           Billers mobile                                                                                            |                                            default: `nill` |
| `billingName`                        |                                                                                            Billers Name                                                                                             |                                            default: `nill` |
| `channels`                           | Specify payment options available to users. Available channel options are: ["card", "bank", "ussd", "qr", "mobile_money"]. Here's an example of usage: `channels={JSON.stringify(["card","ussd"])}` |                                          default: `"card"` |
| `onCancel`                           |               callback function if user cancels or payment transaction could not be verified. In a case of not being verified, transactionRef number is also returned in the callback               |                                            default: `nill` |
| `onSuccess`                          |                                    callback function if transaction was successful and verified (it will also return the transactionRef number in the callback )                                    |                                            default: `nill` |
| `autoStart`                          |                                                                               Auto start payment once page is opened                                                                                |                                           default: `false` |
| `SafeAreaViewContainer`              |                                                                                  style for SafeAreaView containter                                                                                  |                                            default: `nill` |
| `SafeAreaViewContainerModal`         |                                                                                  style for SafeAreaView for modal                                                                                   |                                            default: `nill` |
| `showPayButton`                      |                                                                                Control the Pay Now button visibility                                                                                |                                            default: `true` |
| `refNumber`                          |                                                                         Reference number, if you have already generated one                                                                         | default: `''+Math.floor((Math.random() * 1000000000) + 1)` |
| `renderButton`                       |                                                            Render your own Pay Now button, should be used when `showPayButton` is `true`                                                            |                                            default: `null` |
| `handleWebViewMessage`               |                                                                          Will be called when a WebView receives a message                                                                           |                                            default: `true` |

## [](https://github.com/just1and0/object-to-array-convert#contributions)Contributions
 
### Don't forget to star, like and share :)

## Contributors ✨
 - Kayode Olayiwola

