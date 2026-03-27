# Product Details Snippet Configuration

The `product-details-snippet.liquid` has been created and integrated into your product template. To make it configurable through the Shopify theme editor, you need to add settings and block types to your main product section.

## Step 1: Add Settings to Product Section

Add these settings to `sections/product.liquid` in the `settings` array (around line 200-300):

```json
{
  "type": "header",
  "content": "Product Details Settings"
},
{
  "type": "select",
  "id": "product_details_style",
  "options": [
    {
      "value": "tabs",
      "label": "Tabs"
    },
    {
      "value": "collapsible-rows",
      "label": "Collapsible Rows"
    }
  ],
  "default": "collapsible-rows",
  "label": "Product Details Style"
},
{
  "type": "checkbox",
  "default": false,
  "id": "expand_first_product_detail",
  "label": "Expand First Detail Row",
  "info": "Only applies to collapsible rows style"
}
```

## Step 2: Add Block Types to Product Section

Add these four block types to the `blocks` array in `sections/product.liquid` (before the closing `]` of blocks, around line 5600):

```json
{
  "type": "product_detail_description",
  "name": "Product Detail - Description",
  "limit": 1,
  "settings": [
    {
      "type": "text",
      "id": "title",
      "default": "Description",
      "label": "Title"
    },
    {
      "type": "select",
      "id": "icon",
      "options": [
        {"value": "none", "label": "None"},
        {"value": "document", "label": "Document"},
        {"value": "information", "label": "Information"}
      ],
      "default": "none",
      "label": "Icon"
    },
    {
      "type": "image_picker",
      "id": "custom_icon_image",
      "label": "Custom Icon Image"
    }
  ]
},
{
  "type": "product_detail_collapsible_row",
  "name": "Product Detail - Content Tab",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "default": "Content tab",
      "label": "Title"
    },
    {
      "type": "select",
      "id": "icon",
      "options": [
        {"value": "none", "label": "None"},
        {"value": "document", "label": "Document"},
        {"value": "information", "label": "Information"}
      ],
      "default": "none",
      "label": "Icon"
    },
    {
      "type": "image_picker",
      "id": "custom_icon_image",
      "label": "Custom Icon Image"
    },
    {
      "type": "richtext",
      "id": "text",
      "label": "Text"
    },
    {
      "type": "page",
      "id": "page",
      "label": "Page"
    },
    {
      "type": "image_picker",
      "id": "image",
      "label": "Image"
    },
    {
      "type": "video",
      "id": "video",
      "label": "Video"
    },
    {
      "type": "range",
      "id": "image_width",
      "min": 10,
      "max": 100,
      "step": 5,
      "default": 100,
      "unit": "%",
      "label": "Image Width"
    }
  ]
},
{
  "type": "product_detail_faq",
  "name": "Product Detail - FAQ",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "default": "FAQ",
      "label": "Title"
    },
    {
      "type": "select",
      "id": "icon",
      "options": [
        {"value": "none", "label": "None"},
        {"value": "information", "label": "Information"}
      ],
      "default": "none",
      "label": "Icon"
    },
    {
      "type": "image_picker",
      "id": "custom_icon_image",
      "label": "Custom Icon Image"
    },
    {
      "type": "text",
      "id": "question1",
      "label": "Question 1"
    },
    {
      "type": "richtext",
      "id": "answer1",
      "label": "Answer 1"
    },
    {
      "type": "text",
      "id": "question2",
      "label": "Question 2"
    },
    {
      "type": "richtext",
      "id": "answer2",
      "label": "Answer 2"
    },
    {
      "type": "text",
      "id": "question3",
      "label": "Question 3"
    },
    {
      "type": "richtext",
      "id": "answer3",
      "label": "Answer 3"
    },
    {
      "type": "text",
      "id": "question4",
      "label": "Question 4"
    },
    {
      "type": "richtext",
      "id": "answer4",
      "label": "Answer 4"
    },
    {
      "type": "text",
      "id": "question5",
      "label": "Question 5"
    },
    {
      "type": "richtext",
      "id": "answer5",
      "label": "Answer 5"
    }
  ]
},
{
  "type": "product_detail_custom_liquid",
  "name": "Product Detail - Custom Liquid",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "default": "Custom",
      "label": "Title"
    },
    {
      "type": "select",
      "id": "icon",
      "options": [
        {"value": "none", "label": "None"},
        {"value": "settings", "label": "Settings"}
      ],
      "default": "none",
      "label": "Icon"
    },
    {
      "type": "image_picker",
      "id": "custom_icon_image",
      "label": "Custom Icon Image"
    },
    {
      "type": "liquid",
      "id": "custom_liquid",
      "label": "Custom Liquid Code"
    }
  ]
}
```

## How It Works

1. The snippet reads the `product_details_style` setting to determine whether to show tabs or collapsible rows
2. It filters section blocks to find only the product detail block types (`product_detail_description`, `product_detail_collapsible_row`, `product_detail_faq`, `product_detail_custom_liquid`)
3. These blocks appear in the theme customizer under "Product details" section when you add them

## Usage in Theme Editor

After adding these to your product section schema:

1. Go to the theme customizer
2. Navigate to a product page  
3. Click on the Product section
4. You'll see:
   - "Product Details Settings" to choose tabs vs collapsible rows
   - "Add block" button to add product detail blocks
   - Each block type will appear with its name (Description, Content Tab, FAQ, Custom Liquid)

The product details will appear below the product images on the left side, with the product info staying sticky on the right.
