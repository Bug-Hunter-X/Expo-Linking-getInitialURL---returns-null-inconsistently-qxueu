# Expo Linking.getInitialURL() Returns Null Inconsistently

This repository demonstrates a bug in Expo's `Linking.getInitialURL()` API. The function sporadically returns `null`, even when the application is launched via a deep link. This makes it impossible to reliably handle deep links using the standard Expo methods.

## Reproducing the bug

Follow the steps below to reproduce the issue:
1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the app on both a physical device and emulator.
4. Launch the app using a deep link (e.g., `myapp://link`).
5. Observe that `getInitialURL` sometimes returns null, and sometimes return the expected URL. This is inconsistent and difficult to debug. 

## Proposed Solution

The solution involves using a more robust method to handle deep links, which involves listening for URL changes and handling initial URL retrieval within the app's lifecycle. The provided solution uses `Linking.addEventListener` to reliably listen for the URL event. 

## Additional Notes

This bug has been observed across several Expo SDK versions and device types, pointing towards a potential issue within the Expo Linking API itself. It is essential to have a reliable mechanism for handling deep links in any Expo application, and this solution provides an alternative approach.