
<img src="https://raw.githubusercontent.com/Trendyol/android-ui-components/master/images/quantity-picker-view-1.gif" />

$quantityPickerViewVersion = quantity-picker-view-1.0.1 [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## QuantityPickerView
QuantityPickerView is component for add/remove

## Installation
  - To implement **QuantityPickerView** to your Android project via Gradle, you need to add JitPack repository to your root/project level build.gradle.
```gradle
allprojects {  
 repositories { ... maven { url 'https://jitpack.io' } }}  
```
 - After adding JitPack repository, you can add **QuantityPickerView** dependency to your app/module level build.gradle.
```gradle
dependencies {  
 implementation "com.github.Trendyol.android-ui-components:quantity-picker-view:$quantityPickerViewVersion"}
```
:warning: To use **QuantityPickerView**, you have to enable dataBinding from your project's `build.gradle`.

## Usage
You can inflate **QuantityPickerView** via XML or programmatically. View can be configurable either in XML or setting a *QuantityPickerViewState*.

To set programmatically, you can call `QuantityPickerView.setQuantityPickerViewState(QuantityPickerViewState)`.

| Attribute |  Method | Description | Default Value |
| ------------- | ------------- | ------------- | ------------- |
| qpv_text | text | Text to show when currentQuantity is 0. | "" |
| qpv_textColor | textColor |  Text color. | `orange |
| qpv_textSize | textSize | Text size. Should be pixel value if programmatically set. | 12sp |
| qpv_textStyle | textStyle | Text style: normal(0), bold(1) or italic(2) Note: Default text font is Roboto Medium. | normal |
| qpv_quantityTextColor | quantityTextColor | Quantity text color. | `gray |
| qpv_quantityTextSize | quantityTextSize | Quantity text size. Should be pixel value if programmatically set.  | 14sp |
| qpv_quantityTextStyle | quantityTextStyle | Quantity text style: normal(0), bold(1) or italic(2) Note: Default text font is Roboto Medium. | normal |
| qpv_currentQuantity | currentQuantity | Quantity value, optional. | 0 |
| android:progressTint | progressTintColor | Tint for loading ProgressBar. | `orange |
| android:background | backgroundDrawable | Background to all view. | [qpv_shape_default_background.xml](src/main/res/drawable/qpv_shape_default_background.xml) |
| qpv_removeIcon | removeIconDrawable | Icon for remove, will be only visible when currentQuantity is 1. | [qpv_ic_default_remove.xml](src/main/res/drawable/qpv_ic_default_remove.xml) |
| qpv_addIcon | addIconDrawable | Icon for add, will be visible when currentQuantity is 1 or more. | [qpv_ic_default_add.xml](src/main/res/drawable/qpv_ic_default_add.xml) |
| qpv_subtractIcon | subtractIconDrawable | Icon for subtract, will be visible when currentQuantity is 2 or more. | [qpv_ic_default_subtract.xml](src/main/res/drawable/qpv_ic_default_subtract.xml) |

# Public methods

| Method Name |  Parameter | Description |
| ------------- | ------------- | ------------- |
| setQuantityPickerViewState | viewState :QuantityPickerViewState | To set QuantityPickerViewState programmatically. |
| setQuantity | quantity: Int | To set quantity immediately. |
| stopLoading |  | To stop current loading |
| reset |  | To stop loading and set currentQuantity to 0. |

## Listeners
To get updates on **QuantityPickerView** you need to set this listeners:

| Listener | Data | Return | Information |
| ------------- | ------------- | ------------- | ------------- |
| onAddClicked | quantityAfterAdd: Int | showLoading: Boolean | Will be triggered when user clicks text when currentQuantity 0 or add button when currentQuantity bigger than 0. |
| onSubtractClicked | quantityAfterSubtract: Int | showLoading: Boolean | Wil be triggered when user clicks remove or subtract icon. |

## Implementation

From XML, you can use attributes like below:

```xml
<com.trendyol.uicomponents.quantitypickerview.QuantityPickerView
    android:id="@+id/quantity_picker_view"
    android:layout_width="match_parent"
    android:layout_height="36dp"
    app:qpv_quantityTextSize="14sp"
    app:qpv_text="Add to Basket"
    app:qpv_currentQuantity="1"
    app:qpv_textSize="12sp" />
```

To set *QuantityPickerViewState* programmatically:

```kotlin
val viewState = QuantityPickerViewState(
    text = "Fresh Money",
    textSize = (12 * resources.displayMetrics.scaledDensity).toInt(),
    quantityTextSize = (14 * resources.displayMetrics.scaledDensity).toInt(),
    backgroundDrawable = ContextCompat.getDrawable(this, R.drawable.shape_quantity_background)!!,
    removeIconDrawable = ContextCompat.getDrawable(this, R.ic_remove)!!,
    subtractIconDrawable = ContextCompat.getDrawable(this, R.drawable.ic_minus)!!,
    addIconDrawable = ContextCompat.getDrawable(this, R.drawable.ic_add)!!
)
        
findViewById<QuantityPickerView>(R.id.quantity_picker_view).setQuantityPickerViewState(viewState)
```

## Contributors
This library is maintained mainly by Trendyol Android Team members but also other Android lovers contributes.

We developed this component for our needs, there is lots of improvements need to be implemented.

# License
    Copyright 2020 Trendyol.com

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
