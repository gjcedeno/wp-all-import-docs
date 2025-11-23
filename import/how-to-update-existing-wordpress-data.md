# How to Update Existing WordPress Data

To update existing WordPress data, create an import via **All Import › New Import**.

Provide your import file, choose the required post type, then configure WP All Import to match with existing records.

## Table of Contents

- [How Updating WordPress Data Works](#how-updating-wordpress-data-works)
- [Step 1: Understanding the Import Data](#step-1-understanding-the-import-data)
- [Step 2: Set Up the Import](#step-2-set-up-the-import)
- [Step 3: Fill In Data to Update in the Import Template](#step-3-fill-in-data-to-update-in-the-import-template)
- [Step 4: Specify Important Import Settings](#step-4-specify-important-import-settings)

## How Updating WordPress Data Works

WP All Import can import data to posts that already exist on your site, even if they were manually created instead of imported by our plugin.

You need something in your import file that WP All Import can use to match the records in your import file to the posts that already exist on your site — that’s why it's also called **Manual Record Matching**.

When importing into existing records, you can specify which data WP All Import will update or overwrite, and which will be left alone.

Follow along with the example below to get a complete understanding of how to import data into existing posts.


## Step 1: Understanding the Import Data

This example demonstrates how to update multiple property listings with new prices.

On your site, you have a few property listings with outdated prices.

You also have a CSV file with:

- The MLS numbers of the properties.
- The new prices.

The MLS number of each property has been entered in your theme. This means we can use the MLS number as the “matcher” so that WP All Import knows which price should be assigned to which property.


## Step 2: Set Up the Import

To create the import:

1. Navigate to **All Import › New Import**.
2. Upload your CSV file.
3. Select **Property Listings** as the post type.

Click **Set Up Import** to continue.


## Step 3: Fill In Data to Update in the Import Template

In the **Drag & Drop** section:

1. Set the **price** custom field to the price from your file.
2. Leave all the other fields blank, since the only field we want to update is the price.

WP All Import will warn you that your post title and content are blank, but that’s fine — you can continue anyway.

Click **Continue to Import Settings** at the bottom.


## Step 4: Specify Important Import Settings

Now it’s time for the most important part — telling WP All Import how to match the records in your CSV file with the existing property listings already on your site.

We’re going to match by the **MLS number**, since we have the MLS number both on our site and in our import file.

### Define How to Match with Existing Data

In **Import Settings**, select:

> **Attempt to match to existing WordPress posts before creating new ones.**

Then:

1. Choose to match based on **Custom field**.
2. In the **Name** box, enter `mls_value`, which is the custom field used to store the MLS number for each property.
3. Drag & drop the **MLS** column from your CSV file to the **Value** textbox.

For each record in your file, the plugin will look for a property on your site with an `mls_value` custom field that equals the same as `{mlsno[1]}` from your file, and then import the price to it.

> If you have multiple records or properties with this same value, only the first found record will be matched and updated.  
> To match multiple properties that share the exact same `mls_value`, custom code must be used along with our API.

### Tell WP All Import Exactly Which Fields to Update

To ensure the plugin only imports the price and doesn’t overwrite the title, content, and other fields that you left empty:

1. Go to the **Choose which data to update** section.
2. Specify that only the `price_value` custom field should be updated.

If the custom field to update doesn’t appear in the dropdown list, you can type it in manually and press **Return/Enter** to add it.

> This step is very important. If you choose to update all data without having data mapped, you risk erasing existing data from your posts. Only continue after defining exactly which fields to update.

Once everything is set up, click **Continue** and then **Confirm & Run Import**.

After running the import, your posts will be updated with the new prices.

That’s how you use **Manual Record Matching**.

