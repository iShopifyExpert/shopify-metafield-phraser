# shopify-metafield-phraser

> Also known as: `metafield-richtext-renderer`  
> 🛍️ A Shopify snippet to transform structured JSON metafields into clean, renderable HTML.

---

## 📌 What it does

  Shopify metafields (especially `rich_text` ones) often return structured JSON like this:

    {
      "type": "root",
      "children": [
        {
          "type": "paragraph",
          "children": [
            {
              "type": "text",
              "value": "The MS530M Brush Mulcher is a heavy-duty, versatile Mini Skidsteer mulcher built for efficient mulching and clearing of brush, trees, and vegetation."
            }
          ]
        }
      ]
    }
    
This snippet parses and converts such metafield JSON data into proper HTML. It supports:

Paragraphs (<p>)
Lists (ordered and unordered)
Bold text (<strong>)
Hyperlinks (<a href>)

✅ When to use it
Use this snippet when you have rich_text metafields on products or collections and want to render them directly in your Shopify theme.

Example metafield call in your template or section:

{{ product.metafields.custom.short_description.value }}
If that outputs raw JSON, use this snippet to parse and render it correctly.

🛠️ How to install
Create a new snippet file in your Shopify theme:
snippets/shopify-metafield-phraser.liquid

Paste the full rendering code inside it (see code in this repo).

Use the snippet like this wherever you want the metafield HTML to appear:

{% render 'shopify-metafield-phraser', product-metafield: product.metafields.custom.short_description.value %}
You can pass in any rich_text metafield, including for collections, blog articles, etc.

💬 Output example
Given a metafield like this:

    {
      "type": "root",
      "children": [
        {
          "type": "paragraph",
          "children": [
            {
              "type": "text",
              "value": "For machines equipped 12–20 gpm or for 40–60 hp machines"
            }
          ]
        }
      ]
    }
The output will be:

<p>For machines equipped 12–20 gpm or for 40–60 hp machines</p>

📄 License
MIT – free to use, share, and modify.
