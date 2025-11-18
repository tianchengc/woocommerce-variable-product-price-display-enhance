# woocommerce-variable-product-price-display-enhance

A repository dedicated to providing a simple, quick fix to change the confusing price range display (e.g., "$100 – $250") to use default/minimum price for WooCommerce variable products on shop and archive pages.

This solution uses pure CSS and does not require editing theme files or adding complex PHP.

## 🎯 The Problem

By default, WooCommerce variable products display prices on shop and archive pages as a range (e.g., **$100 – $250**). This presentation can be confusing to customers and often leads to lower click-through rates by showcasing the highest potential price first.

This fix eliminates the range, leaving only the lowest price visible.

## ✅ The Solution: Precision CSS Snippet

This code snippet uses precise CSS selectors to target the price separator (the dash) and the maximum price amount, hiding them from view and leaving only the minimum price. This avoids interfering with the display of single, non-variable products.

### Code to Use

Use this code exactly as shown below:

```css
/*
 * Hides the price separator and the maximum price amount
 * for WooCommerce variable products in shop loops.
 */
.price > span:nth-child(2) {
    display: none!important; /* Targets the price separator (the dash) */
}

.price > span:nth-child(3) {
    display: none!important; /* Targets the third span which holds the maximum price */
}
```

### ⚙️ How to Implement the Fix

This code should be placed in the safest location for custom styling on any WordPress installation:

1.  Log in to your WordPress Dashboard.
2.  Navigate to **Appearance** -\> **Customize**.
3.  Click on the **Additional CSS** section.
4.  Paste the CSS snippet above into the editor window.
5.  Click the **Publish** button to save and activate the changes immediately.

## 💡 How the Code Works (The Technical Detail)

When WooCommerce displays a price range, it structures the output inside the primary `.price` container as three distinct immediate `<span>` children:

1.  The Minimum Price (e.g., `$100`)
2.  The Separator (e.g., `-`)
3.  The Maximum Price (e.g., `$250`)

The CSS uses the structural pseudo-class selectors to target elements based on their position:

  * `:nth-child(2)` successfully targets the second element, which is the separator.
  * `:nth-child(3)` successfully targets the third element, which is the maximum price.

This prevents the code from accidentally hiding the single price span on non-variable products.

## ⚠️ Important Limitation (Pro Tip for Clarity)

While this CSS solution is an excellent visual quick fix, it only *hides* the unwanted text. It does not dynamically modify the price output.
