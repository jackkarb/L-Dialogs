# L-Dialogs

* * *

A small library replicating the new dialogs in android L.

!["Screenshot 1"](https://github.com/lewisjdeane/L-Dialogs/raw/master/app/src/main/res/screenshots/banner.jpg)

* * *

# Set Up (Android Studio):

Download the aar here: https://www.dropbox.com/s/276bhapr2g50cak/ldialogs.aar?dl=0

Maven central support will be coming soon.

You can rename the aar and then place it in the libs directory of your project.

Go into your build.gradle and add the following:
```java

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'uk.me.lewisdeane.ldialogs:RENAMED_FILE_NAME_HERE@aar'
}

repositories{
    flatDir{
        dirs 'libs'
    }
}

```

# Usage

##Normal Dialogs

You should now be able to access the class CustomDialog from one of your java files.

To create a new CustomDialog we need to use a builder as so:

```java
// Create the builder with required paramaters - Context, Title, Positive Text
CustomDialog.Builder builder = new CustomDialog.Builder(Context context, String title, String positiveText);

// Now we can any of the following methods.
builder.content(String content);
builder.negativeText(String negativeText);
builder.darkTheme(boolean isDark);
builder.titleColor(String hex);
builder.contentColor(String hex);
builder.positiveColor(String hex);
builder.negativeColor(String hex);
builder.titleAlignment(Alignment alignment); // Use either Alignment.LEFT, Alignment.CENTER or Alignment.RIGHT

// Now we can build the dialog.
CustomDialog customDialog = builder.build();

// Show the dialog.
customDialog.show();
```

To handle the button clicks you can use the following code:

```java
customDialog.setClickListener(new CustomDialog.ClickListener() {
            @Override
            public void onConfirmClick() {
                
            }

            @Override
            public void onCancelClick() {

            }
        });
```

If you want to set a custom view in the dialog you can use the following method.

```java
customDialog.setCustomView(View customView);
```

Then do what you need to do with the custom views content in onConfirmClick or onCancelClick.


##List Dialogs

To use the CustomListDialog we need to use a builder again, this is done as follows:

```java
// Create list dialog with required parameters - context, title, and our array of items to fill the list.
CustomListDialog.Builder builder = new CustomListDialog.Builder(Context context, String title, String[] items);

// Now again we can use some extra methods on the builder to customise it more.
builder.titleColor(String hex);
builder.itemColor(String hex);
builder.darkTheme(boolean isDark);
builder.titleAlignment(Alignment alignment); // Use either Alignment.LEFT, Alignment.CENTER or Alignment.RIGHT
builder.itemAlignment(Alignment alignment); // Use either Alignment.LEFT, Alignment.CENTER or Alignment.RIGHT

// Now we can build our dialog.
CustomListDialog customListDialog = builder.build();

// Finally we can show it.
customListDialog.show();
```

In order to recieve the click events from the dialog, simply use the following method on your customListDialog:
```java
customListDialog.setListClickListener(new CustomListDialog.ListClickListener() {
            @Override
            public void onListItemSelected(int i, String[] strings, String s) {
                // i is the position clicked.
                // strings is the array of items in the list.
                // s is the item selected.
            }
        });
``` 

* * *

This library will be updated often, enjoy!
