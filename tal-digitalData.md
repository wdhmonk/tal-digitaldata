# Deploying the New Data Layer Object

This documentation provides instructions on deploying a new `digitalData` object that will populate on page load and during interactions with specific elements on your website. The `digitalData` pushes are the same object, with the `event` value differing based on whether it's a page load or an interaction with an element.

## Initialising the Data Layer

To initialise the `digitalData` object on your webpage, use the following script:

```javascript
window.digitalData = window.digitalData || [];
```

This script ensures that the `digitalData` array is available for pushing data objects whenever required.

## The `digitalData` Object Structure

Below is the structure of the `digitalData` object that needs to be deployed. This example is for an interaction event:

```javascript
digitalData.push({
  "interaction": {
    "eventType": "button",        // e.g., "navbar", "buttonClick", "formSubmit"
    "clickText": "",              // Text displayed on the clickable element
    "clickURL": "",               // URL the element points to
    "search": {
      "autoSuggestSearchTerm": "",
      "searchTerm": "",
      "searchFilters": "",
      "searchResults": ""
    },                            // Terms entered in search fields
    "cardDescription": "",        // Description of the card if applicable
    "accordionAction": "",        // e.g., "Open" or "Close"
    "interactionSection": "",     // e.g., "header", "footer"
    "userRole": ""                // Specify if user is admin, guest, etc.
  },
  "pageInfo": {
    "pageName": "",
    "pageTitle": "",
    "pageType": "",
    "pageUrl": "",
    "talid": "",
    "mcode": "",
    "referrer": "",               // To be confirmed if this is needed
    "language": "",
    "primaryCategory": "",
    "subCategory1": "",
    "subCategory2": "",
    "subCategory3": "",
    "site": {
      "brand": "",
      "environment": "",
      "domain": ""
    }
  },
  "form": {
    "formName": "",
    "formStep": "",
    "formSubStep": "",
    "quoteId": "",
    "referenceNumber": "",
    "formAction": "",             // For if you go forward or backwards
    "tpdCover": "",
    "traumaCover": "",
    "smoker": "",
    "state": "",
    "postcode": "",
    "occupation": "",
    "age": "",
    "gender": "",
    "amount": "",                 // The cover amount
    "income": "",                 // Income in form
    "lifeCover": "",              // To be defined
    "product": "",                // To be defined
    "vertical": ""                // To be defined
  },
  "user": {
    "email": "",
    "phoneNumber": "",
    "membershipType": "",
    "membershipId": "",
    "loginstatus": "",
    "loginId": "",
    "role": ""
  },
  "event": "interaction"
});
```

---

## Examples for Specific Elements

Below are examples of how to implement the `digitalData` object for various elements, along with sample payloads and images.

### 1. Navigation Bar

When a user interacts with the navigation bar, the `digitalData` object should capture relevant details.

**Example Payload:**

```javascript
digitalData.push({
  "interaction": {
    "eventType": "navbar",
    "clickText": "Home",
    "clickURL": "/home",
    "interactionSection": "header",
    "userRole": "guest"
  },
  "pageInfo": {
    "pageName": "Home Page",
    "pageTitle": "Welcome to Our Website",
    "pageType": "landing",
    "pageUrl": "https://www.example.com/home",
    "language": "en-AU",
    "primaryCategory": "Home",
    "site": {
      "brand": "ExampleBrand",
      "environment": "production",
      "domain": "example.com"
    }
  },
  "event": "interaction"
});
```

**Image Illustration:**

![Navigation Bar Example](path/to/navbar-image.png)

---

### 2. Card

For interactions with cards, such as clicking on a product card, details should be captured accordingly.

**Example Payload:**

```javascript
digitalData.push({
  "interaction": {
    "eventType": "cardClick",
    "cardDescription": "Product XYZ Details",
    "clickText": "Learn More",
    "clickURL": "/products/xyz",
    "interactionSection": "mainContent",
    "userRole": "member"
  },
  "pageInfo": {
    "pageName": "Products Page",
    "pageTitle": "Our Products",
    "pageType": "productListing",
    "pageUrl": "https://www.example.com/products",
    "language": "en-AU",
    "primaryCategory": "Products",
    "subCategory1": "Insurance",
    "site": {
      "brand": "ExampleBrand",
      "environment": "production",
      "domain": "example.com"
    }
  },
  "event": "interaction"
});
```

**Image Illustration:**

![Card Interaction Example](path/to/card-image.png)

---

### 3. Button (CTA)

Capturing interactions with call-to-action buttons is essential for tracking user engagement.

**Example Payload:**

```javascript
digitalData.push({
  "interaction": {
    "eventType": "buttonClick",
    "clickText": "Sign Up Now",
    "clickURL": "/signup",
    "interactionSection": "footer",
    "userRole": "guest"
  },
  "pageInfo": {
    "pageName": "Landing Page",
    "pageTitle": "Join Us Today",
    "pageType": "landing",
    "pageUrl": "https://www.example.com",
    "language": "en-AU",
    "primaryCategory": "Signup",
    "site": {
      "brand": "ExampleBrand",
      "environment": "production",
      "domain": "example.com"
    }
  },
  "event": "interaction"
});
```

**Image Illustration:**

![Button (CTA) Interaction Example](path/to/button-image.png)

---

### 4. Accordion

When users interact with accordion elements, such as expanding or collapsing sections, record the actions.

**Example Payload:**

```javascript
digitalData.push({
  "interaction": {
    "eventType": "accordion",
    "accordionAction": "Open",
    "clickText": "Frequently Asked Questions",
    "interactionSection": "mainContent",
    "userRole": "guest"
  },
  "pageInfo": {
    "pageName": "Help Page",
    "pageTitle": "How Can We Help?",
    "pageType": "support",
    "pageUrl": "https://www.example.com/help",
    "language": "en-AU",
    "primaryCategory": "Support",
    "subCategory1": "FAQ",
    "site": {
      "brand": "ExampleBrand",
      "environment": "production",
      "domain": "example.com"
    }
  },
  "event": "interaction"
});
```

**Image Illustration:**

![Accordion Interaction Example](path/to/accordion-image.png)

---

### 5. Search Bar

For interactions with the search bar, including the terms entered and the results, the data captured helps in understanding user intent and improving search functionality.

**Example Payload:**

```javascript
digitalData.push({
  "interaction": {
    "eventType": "search",
    "search": {
      "searchTerm": "life insurance",
      "autoSuggestSearchTerm": "",
      "searchFilters": "",
      "searchResults": "15"
    },
    "clickText": "Search",
    "interactionSection": "header",
    "userRole": "guest"
  },
  "pageInfo": {
    "pageName": "Search Results",
    "pageTitle": "Search - life insurance",
    "pageType": "searchResults",
    "pageUrl": "https://www.example.com/search?q=life+insurance",
    "language": "en-AU",
    "primaryCategory": "Search",
    "site": {
      "brand": "ExampleBrand",
      "environment": "production",
      "domain": "example.com"
    }
  },
  "event": "interaction"
});
```

**Image Illustration:**

![Search Bar Interaction Example](path/to/searchbar-image.png)

---

## Notes

- **Consistency**: Ensure all data pushed to the `digitalData` object is accurate and consistently formatted.
- **Placeholder Values**: Replace placeholder values (e.g., empty strings, comments) with actual data relevant to the user's interaction and the page context.
- **`referrer` Field**: The `referrer` field in `pageInfo` is optional and subject to confirmation on whether it's needed.
- **Undefined Fields**: Fields such as `lifeCover`, `product`, and `vertical` in the `form` object require clarification and should be defined according to business requirements.

---

By following this guide, you can effectively deploy the `digitalData` object on your website, enabling robust data collection for user interactions and enhancing analytics capabilities.
