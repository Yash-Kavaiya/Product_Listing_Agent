# Product Comparison Agent 🛍️

A powerful AI agent built with Google ADK that performs comprehensive product comparisons with detailed analysis, pricing information, images, and in-depth reports.

## Features ✨

- 🔍 **Intelligent Product Research**: Uses Google Search to gather comprehensive product information
- 📊 **Detailed Comparisons**: Side-by-side feature and specification comparisons
- 💰 **Price Analysis**: Finds best prices across multiple retailers
- 📸 **Image Integration**: Includes product images in comparison reports
- ⚖️ **Pros & Cons Analysis**: Detailed advantages and disadvantages for each product
- 🎯 **Smart Recommendations**: Context-aware suggestions based on use case
- 📈 **Value Scoring**: Calculates value-for-money scores
- 📄 **Multiple Export Formats**: Markdown reports and JSON data export

## Installation 🚀

### Prerequisites

- Python 3.8 or higher
- Google ADK (Agent Development Kit)
- Google Cloud Project with API access

### Setup

1. **Clone the repository:**
```bash
git clone https://github.com/Yash-Kavaiya/Product_Listing_Agent.git
cd Product_Listing_Agent
```

2. **Install dependencies:**
```bash
pip install google-adk
pip install google-auth
pip install google-auth-oauthlib
pip install google-auth-httplib2
```

3. **Set up Google Cloud credentials:**
```bash
# Set your Google Cloud project ID
export GOOGLE_CLOUD_PROJECT="your-project-id"

# Authenticate with Google Cloud
gcloud auth application-default login
```

4. **Enable required APIs:**
- Google Search API
- Vertex AI API

## Usage 💻

### Basic Product Comparison

```python
from productagent.agent import product_comparison_agent

# Simple comparison query
response = product_comparison_agent.query(
    "Compare iPhone 15 Pro and Samsung Galaxy S24 Ultra with detailed specs and images"
)

print(response)
```

### Advanced Comparison with Specific Criteria

```python
query = """
Compare these laptops for software development:
- MacBook Pro 16" M3
- Dell XPS 15
- Lenovo ThinkPad X1 Carbon

Focus on:
- CPU and RAM performance
- Display quality (resolution, color accuracy)
- Battery life during coding
- Port selection
- Keyboard comfort
- Price and value
- Include product images
- Budget: $2000-3000
"""

response = product_comparison_agent.query(query)
print(response)
```

### Using the Report Builder

```python
from productagent.comparison_utils import ProductComparisonReport

# Create a custom report
report = ProductComparisonReport()

# Add products
report.add_product({
    'name': 'Product A',
    'price': '$299',
    'brand': 'Brand X',
    'rating': 4.5,
    'features': {'Feature1': 'Value1', 'Feature2': 'Value2'},
    'pros': ['Pro 1', 'Pro 2'],
    'cons': ['Con 1', 'Con 2']
})

report.add_product({
    'name': 'Product B',
    'price': '$399',
    'brand': 'Brand Y',
    'rating': 4.7,
    'features': {'Feature1': 'Value A', 'Feature2': 'Value B'},
    'pros': ['Pro A', 'Pro B'],
    'cons': ['Con A', 'Con B']
})

# Add comparison criteria
report.add_comparison_criterion('Feature1')
report.add_comparison_criterion('Feature2')

# Add images
report.add_image('https://example.com/image1.jpg', 'Product A Image', 'Product A')
report.add_image('https://example.com/image2.jpg', 'Product B Image', 'Product B')

# Generate report
markdown_report = report.generate_report()
print(markdown_report)

# Export as JSON
json_data = report.to_json()
```

### Running Examples

```bash
# Run all examples
python examples/product_comparison_examples.py

# Or run individual examples by modifying the script
```

## Project Structure 📁

```
Product_Listing_Agent/
├── productagent/
│   ├── __init__.py
│   ├── agent.py                 # Main agent definitions
│   └── comparison_utils.py      # Utility functions for reports
├── examples/
│   └── product_comparison_examples.py  # Usage examples
├── README.md
└── requirements.txt
```

## Agent Capabilities 🤖

The `product_comparison_agent` can:

1. **Research Products**
   - Search for specifications and features
   - Find pricing from multiple sources
   - Locate product images
   - Gather user reviews and expert opinions

2. **Analyze Products**
   - Compare specifications side-by-side
   - Evaluate price-to-performance ratios
   - Assess build quality and materials
   - Consider brand reputation and support

3. **Generate Reports**
   - Executive summaries with quick verdicts
   - Detailed comparison tables
   - Pros and cons for each product
   - Price analysis with best deals
   - Product images with captions
   - Use-case specific recommendations
   - Final verdict with reasoning

## Example Queries 💡

### Smartphones
```
"Compare iPhone 15 Pro and Samsung Galaxy S24 Ultra. Include camera specs, battery life, display quality, and pricing. Show product images."
```

### Laptops
```
"I need a laptop for video editing under $2000. Compare MacBook Pro 14", Dell XPS 15, and ASUS ROG Zephyrus. Focus on GPU, display, and cooling."
```

### Headphones
```
"Compare Sony WH-1000XM5, Bose QuietComfort Ultra, and AirPods Max. Which is best for frequent travelers? Include noise cancellation tests."
```

### Smart Home
```
"Compare Amazon Echo Show 15, Google Nest Hub Max, and Apple HomePod. Consider smart home integration, display quality, and price."
```

## Customization 🔧

### Modify Agent Instructions

Edit `productagent/agent.py` to customize the agent's behavior:

```python
product_comparison_agent = Agent(
    model='gemini-2.0-flash-exp',
    name='product_comparison_agent',
    instruction="""
    Your custom instructions here...
    """,
    tools=[google_search]
)
```

### Add Custom Report Formatting

Extend `productagent/comparison_utils.py` to add custom formatting functions.

## API Reference 📚

### ProductComparisonReport Class

#### Methods:
- `add_product(product_data: Dict)` - Add a product to compare
- `add_comparison_criterion(criterion: str)` - Add a feature to compare
- `add_image(url: str, caption: str, product_name: str)` - Add product image
- `generate_report() -> str` - Generate markdown report
- `to_json() -> str` - Export data as JSON

### Utility Functions:
- `format_product_comparison_report(products_data)` - Format basic report
- `create_comparison_table(products, features)` - Create comparison table
- `format_pros_cons(product_name, pros, cons)` - Format pros/cons section
- `format_image_section(images)` - Format images section
- `calculate_value_score(price, rating, features_count)` - Calculate value score
- `generate_recommendation(products_data)` - Generate recommendations

## Best Practices 🌟

1. **Be Specific**: Clearly state which products you want to compare
2. **Define Criteria**: Mention specific features that matter to you
3. **Set Budget**: Include your budget range for better recommendations
4. **Request Images**: Explicitly ask for images if you want visual comparisons
5. **Specify Use Case**: Mention your intended use (gaming, work, travel, etc.)
6. **Multiple Sources**: Ask for price comparisons across retailers

## Troubleshooting 🔧

### Common Issues

**Issue**: Agent not finding products
- Solution: Be more specific with product names and models

**Issue**: No images in report
- Solution: Explicitly request "include product images" in your query

**Issue**: Missing price information
- Solution: Specify retailers or regions for pricing

**Issue**: API rate limits
- Solution: Add delays between queries or use a higher quota

## Contributing 🤝

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License 📄

This project is licensed under the MIT License.

## Support 💬

For issues and questions:
- Open an issue on GitHub
- Contact: [your-email@example.com]

## Acknowledgments 🙏

- Built with [Google ADK](https://cloud.google.com/vertex-ai/docs/agents)
- Uses Google Search for product research
- Powered by Gemini AI models

## Roadmap 🗺️

- [ ] Add support for video comparisons
- [ ] Integrate with e-commerce APIs for real-time pricing
- [ ] Add user review sentiment analysis
- [ ] Support for multi-language comparisons
- [ ] Export reports to PDF
- [ ] Interactive web dashboard

---

Made with ❤️ by [Yash Kavaiya](https://github.com/Yash-Kavaiya)
