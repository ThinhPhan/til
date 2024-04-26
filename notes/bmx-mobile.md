# BMX Mobile

## ToC

* BMX Mobile
  * Plan
  * API
    * Update
    * New API
  * Authenticate
    * Bug
  * Home
  * Wallet
  * Deposit
  * Withdraw
  * Exchange
  * Profile
  * History
  * Referral
  * Notification
  * Forgot Password
  * FIXED
  * Validate
    * Biometrics - FaceID, TouchID
      * References
    * 23/8/2021

## Plan

`2.8 -> 12pm 6.8`

**2.8**

* Wallet
* Deposit
* Withdraw
* Exchange
* Home

**3.8**

* Waiting for API document, implementation
* Update flow Auth with no depend on email \(sendgrid template fraud\)

## API

* [x] 3h hom nay update

### Update

* [x] get\_rate -&gt; fake tren firebase \(nhap tay cac coins\)
* currencies
  * [x] Bo sung symbol icon \(png\)
  * [x] them `exchange fee`,
  * [x] memo cho Swingby
* [ ] response loi theo language tu api
* [ ] profile: verified\_email, verified\_phone, language
* [x] histories: them pagination

### New API

* [ ] Withdraw
* [ ] exchange
* [ ] bmx module

### Authentication

1. Sign in Còn lỗi chưa có thông báo nếu user chưa confirm email thì cần hiện thông báo chưa confirmation và không sign-in được \(?? chưa chốt\)
2. Signup -&gt; Check email chua work do sendgrid -&gt; workaround
3. Forgot Pass Send email -&gt; change pass on web browser -&gt; login with new pass \(skip step change pass on phone\)

#### Bug

**Update 5.8**

* [ ] Input entrance code -&gt; finger icon have weird animation -&gt; maybe async detect biometric **support**
* [ ] Case `Multi User` -&gt; if user login another account -&gt; what about pincode ??? -&gt; setup again new code with new user
* [ ] Handle null data \(fetching error or server return null ....\)
* [ ] Calculate height for `Referral -> Commission History`, screen not auto height
* [ ] Co che de reset pin code khi quen ???
* [ ] Token expired -&gt; Handle in global state

### Home

* [x] Fetch data from API: name
* [x] Avatar -&gt; Gửi default ava place holder
* [x] Chuông =&gt; Notification in app - Screen thông báo notification giống binance \( Như hình Quinn gửi\)
* [x] Hình banner gửi hình ratio giống figma -&gt; API se gui hinh theo ratio nhu figma
* [x] Total Value
  * [x] Total Wallet Balances in BTC/USD \(rate fake from Firebase\)
* [ ] Total Earning
  * [ ] API Needed
  * [x] View Details -&gt; History \(Earning\)
  * [x] Keep fake data: %, progress, chart , change -0.32 -&gt; +0.32
* [x] BMX widget -&gt; BMX Tab

### Wallet

* [x] Screen chi tiết của wallet. Bấm vào đồng thì hiện ra detail của đồng \( Hình Dương gửi\)
* [x] Click vao trang detail
* [x] Deposit/ withdraw list coin dùng API currency để xuất ra
* [x] Screen chi tiết của từng coin trả API dữ liệu detail ở trong chính xác về address, QR code. Riêng swingby có thêm memo

### Deposit

* [x] `Swingby` -&gt; show them memo giong `deposit address`
* [x] Show data dung theo api
* [x] List coins lay tu `/currencies`

### Withdraw

* [x] Update fetch data
* [ ] API chua co -&gt; document \(request, response, 1 so error can biet\)
* [ ] Withdraw Verification ?? `Gmail / 2FA`

**Update - 4/8**

1. [x] Swingby chua cho withdraw -&gt; `@Duong` bo sung field de check
2. [x] `Commission Fee` -&gt; `@Duong` bo sung API
3. [x] `transaction_fee = commission_fee (withdraw_usdt_fee) / currency_rate` \(don vi la currency\_symbol\)
4. [x] total = amount user input + trans fee

### Exchange

* [x] API -&gt; deploy at `11:41 19/08` @Duong, fixing `POST`
* [x] Get: chi nhan: `BMX | Swingby | B21`
* [x] Pay: `allow_buy_crypto`
* [x] To: `allow_exchange`
* [x] `Pay` va `To` ko dc trung coin nhau
* [x] **estimate  = rate - exchange\_fee \(= markup rate -&gt; @Duong note calculate\)**
* [x] History vao exchange

**19/8 Update**

* @Duong deploy `/exchange` -&gt; GET, POST
* Fixing lai `POST` client ko gui `rate: resource_usd_rate | target_usd_rate` vao trong `request body`, rate cho transaction se do Backend tu get realtime tai thoi diem transaction dien ra.

**Notice** Rate cho USDT tinh khac so voi cac currency khac

* Ko co `markup_fee`
* Fixed rate `USDT` = 1

```javascript
if (resource_currency == "USDT") {
  var rate = 1 / parseFloat(rate_target_usd);
} else {
  var rate =
    parseFloat(rate_resource_usd) /
    (parseFloat(rate_target_usd) * parseFloat(markup_fee));
}
```

### Profile

**17/8 New request**

* Security - Add Google 2FA

### History

* [x] API fetch data

### Referral

* [x] Referral QR -&gt;  Show QRCode image `Referral URL`

### Notification

* [x] Screen UI
* [x] List Empty **Data**

**17/8 New request**

* [x] Add Detail Notification Screen -&gt; Mockup UI only -&gt; waiting for API and update later

### Forgot Password

* [ ] Sua password tren web -&gt;  back lai app -&gt; login voi pass moi sua \(ko sua pass tren app\)

### FIXED

* [x] 41 - Exchange -&gt; tick symbol duplicate
* [x] 42 - Nhập amount pay nhưng không ra được amount get \(estimated\)
* [x] 60 - Notification
* [x] 67 27 - Tab bar overlap
* [x] 18 66 - Entrance code style
* [x] 81
* [x] 82
* [x] 84
* [x] 72
* [x] 83, 86
* [x] 85
* [x] 79, 69
* [x] 87
* [x] 73
* [x] 30
* [x] 59
* [x] 73
* [x] 86
* [x] 88

```javascript
{
  "email": "qa.test231193@gmail.com",
  "password": "naru2311"
}
```

### Validate

* [https://stackoverflow.com/questions/14850553/javascript-regex-for-password-containing-at-least-8-characters-1-number-1-uppe](https://stackoverflow.com/questions/14850553/javascript-regex-for-password-containing-at-least-8-characters-1-number-1-uppe)
* [https://www.section.io/engineering-education/password-strength-checker-javascript/](https://www.section.io/engineering-education/password-strength-checker-javascript/)
* [https://www.thepolyglotdeveloper.com/2015/05/use-regex-to-test-password-strength-in-javascript/](https://www.thepolyglotdeveloper.com/2015/05/use-regex-to-test-password-strength-in-javascript/)

```text
/^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])[0-9a-zA-Z]{8,}$/
Here is an explanation:

/^
  (?=.*\d)          // should contain at least one digit
  (?=.*[a-z])       // should contain at least one lower case
  (?=.*[A-Z])       // should contain at least one upper case
  [a-zA-Z0-9]{8,}   // should contain at least 8 from the mentioned characters
$/
```

### Biometric Authentication - FaceID, TouchID

#### Prerequisites <a id="title1.1"></a>

First, you need to make sure your device supports biometric authentication.

You should always make sure that you're running the most recent version of Dashlane for your device. Check to see if there's an [update available on the Play Store.](https://google.com)

Lastly, you need to make sure that your device itself uses a lock-screen \(PIN or fingerprint\) to be able to enable app's biometric authentication.

`Hardware Device Support` -&gt; `Support Types (Face/Touch)` -&gt; `isEnrolled` -&gt; `isEnrolledLevel` -&gt;

1. Entrance Code:
   * If `PIN` code is already set
   * If `Biometric` support **AND** `Allow Biometric` in `Security`
2. `Signup` -&gt; Check Email -&gt; `Setup Entrance Code` -&gt; `Setup Biometric`
   * Enable `Biometric` in last step
3. Signin -&gt; Entrance \(1\)
4. Security -&gt; `Biometric`
   * Enable/Disable `Biometric`

```javascript
const savedBiometrics = await LocalAuthentication.isEnrolledAsync()
    if (!savedBiometrics)
      return Alert.alert(
        "Biometric record not found",
        "Please verify your identity with your password",
        [
          {
            text: "OK",
            onPress: () => null,
            style: "default",
          },
        ],
        // () => fallBackToDefaultAuth(),
      )
```

**References**

* [https://developer.apple.com/documentation/localauthentication](https://developer.apple.com/documentation/localauthentication)
* [https://developer.apple.com/documentation/localauthentication/accessing\_keychain\_items\_with\_face\_id\_or\_touch\_id](https://developer.apple.com/documentation/localauthentication/accessing_keychain_items_with_face_id_or_touch_id)
* [https://developer.apple.com/documentation/localauthentication/logging\_a\_user\_into\_your\_app\_with\_face\_id\_or\_touch\_id](https://developer.apple.com/documentation/localauthentication/logging_a_user_into_your_app_with_face_id_or_touch_id)
* [https://github.com/naoufal/react-native-touch-id](https://github.com/naoufal/react-native-touch-id)
* [https://github.com/SelfLender/react-native-biometrics](https://github.com/SelfLender/react-native-biometrics) - Use Biometrics to authenticate stored keys
* [https://support.dashlane.com/hc/en-us/articles/203682911-How-to-set-biometric-authentication-or-a-PIN-code-to-unlock-Dashlane-on-Android](https://support.dashlane.com/hc/en-us/articles/203682911-How-to-set-biometric-authentication-or-a-PIN-code-to-unlock-Dashlane-on-Android)
* [https://support.dashlane.com/hc/en-us/articles/208040269-How-to-set-up-biometric-authentication-or-a-PIN-code-to-unlock-Dashlane-on-iPhone-and-iPad](https://support.dashlane.com/hc/en-us/articles/208040269-How-to-set-up-biometric-authentication-or-a-PIN-code-to-unlock-Dashlane-on-iPhone-and-iPad)
* [https://blog.logrocket.com/how-to-implement-faceid-and-touchid-in-react-native-and-expo/](https://blog.logrocket.com/how-to-implement-faceid-and-touchid-in-react-native-and-expo/)

Bottom Sheet - Customize

* [https://github.com/enesozturk/rn-swipeable-panel](https://github.com/enesozturk/rn-swipeable-panel)
* [https://github.com/osdnk/react-native-reanimated-bottom-sheet](https://github.com/osdnk/react-native-reanimated-bottom-sheet) - 2.9K
* [https://github.com/gorhom/react-native-bottom-sheet](https://github.com/gorhom/react-native-bottom-sheet) - 2.1K
* [https://github.com/rgommezz/react-native-scroll-bottom-sheet](https://github.com/rgommezz/react-native-scroll-bottom-sheet)
* [https://github.com/nomi9995/react-native-bottomsheet-reanimated](https://github.com/nomi9995/react-native-bottomsheet-reanimated)
* [https://github.com/nysamnang/react-native-raw-bottom-sheet](https://github.com/nysamnang/react-native-raw-bottom-sheet) - 846
* [https://github.com/StefanoMartella/react-native-simple-bottom-sheet](https://github.com/StefanoMartella/react-native-simple-bottom-sheet) - 27

## Time Logs

### 2021.08.23

* [ ] Setup 2FA Google Authenticator for withdraw
* [ ] Exchange API implementation
* [ ] BMX screens mockup -&gt; T6
* [ ] BMX APis
  * [ ] Info
  * [ ] Projects
  * [ ] Records
  * [ ] GET/bmx/unstake
  * [ ] POST /bmx/purchase

### 2021.08.24

### 2021.08.26

React Native + TypeScript + MobX

**Issue**: Trouble to understand concept and implement when developing application handle logic between APIs and Store - decoupling the dependency

**References**:

* [Well explain architecture and setup project with TS + Mobx + MST](https://dev.to/shevchenkonik/react-typescript-mobx-4mei)
*
**Issue**: Above issue link to this `Domain Area` mentioned in article -&gt; `Axios/Apisauce`, `TypeScripts`, `MST`,  `MobX`

## Issues: `Apisauce/Axios` + `MST` + `MobX`

* Cancel
* Retry when timeout or network error

1. How to cancel all API requests \(use case handle 401 Unauthorize - token expired and need direct to login screen\) in `apisauce - axios wrapper`

* [https://stackoverflow.com/questions/66180597/cancelling-upload-request-before-destroying-object-makes-mobx-state-tree-throw-c](https://stackoverflow.com/questions/66180597/cancelling-upload-request-before-destroying-object-makes-mobx-state-tree-throw-c)
* [https://stackoverflow.com/questions/67467875/is-there-any-way-to-cancel-previous-async-action-in-mobx-state-tree-similar-to](https://stackoverflow.com/questions/67467875/is-there-any-way-to-cancel-previous-async-action-in-mobx-state-tree-similar-to)
* [https://stackoverflow.com/questions/68862020/react-mobx-with-mst-refresh-token-implement-logic](https://stackoverflow.com/questions/68862020/react-mobx-with-mst-refresh-token-implement-logic)
* [https://github.com/axios/axios/issues/1497](https://github.com/axios/axios/issues/1497)
* [https://lifesaver.codes/answer/cancel-request-if-a-subsequent-request-is-made](https://lifesaver.codes/answer/cancel-request-if-a-subsequent-request-is-made)
* [https://www.leighhalliday.com/use-effect-hook](https://www.leighhalliday.com/use-effect-hook) - UseEffect with Axios Cancel Request
* [Cancelling HTTP Requests with React Hooks and Axios!](https://www.youtube.com/watch?v=fhu1z5oRxC8)

Note: Better with MST. Current solution is hook MST rootStore into api-service to call logout \(rootStore.authStore.logout\(\)\) - little bit workaround, not a overral approach and decouple way to do.
