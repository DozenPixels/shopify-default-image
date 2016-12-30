##**Shopify** - Default Product Image

Shopify handles products without images in a bit of strange way, as there is no way to set a defualt image in settings. This is a quick way to fix this problem and requires editing two template files.

---

####Step 1

Upload your default image to the **Assets** folder with the name *coming-soon.png*.

####Step 2

Open your *snippet-product-item.liquid* file in the **Snippets** folder and add the following code inside the `<a href="">` tag for your product image before any `<img>` tags and right above the first `{% if %}` statement.

```
{% if product.images.size == 0 %}
  {{ 'coming-soon.png' | asset_url | img_tag }}
{% else %}
```

####Step 3

Repeat the above steps in the *product.liquid* file by pasting the following code:

```
{% if product.images.size == 0 %}
  {{ 'coming-soon.png' | asset_url | img_tag }}
{% else %}
```

Depending on your theme, you might not have an `<a href="">` that houses your image. Alternatively look for the image container, possibly a div that contains an `<img>` tag with liquid syntax `{{ image.src | product_img_url: 'grande' }}` and paste the code above. Make sure you add a closing `{% endif %}` following the closing `</img>` tag to end the statement.