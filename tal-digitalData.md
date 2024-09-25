# Deploying the New Data Layer Object

This documentation provides instructions on deploying a new `digitalData` object that will populate on page load and during interactions with specific elements on your website. The `digitalData` pushes are the same object, with the `event` value differing based on whether it's a page load or an interaction with an element.

## Initialising the Data Layer

To initialise the `digitalData` object on your webpage, use the following script:

```javascript
window.digitalData = window.digitalData || [];
```

This script ensures that the `digitalData` array is available for pushing data objects whenever required.

## The `digitalData` Object Structure for event `interaction`

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

## Developer Object Values Types

This will allow for developers to define the object types before pushing to production and encountering any type issues.

```javascript
 {
    interaction: {
      eventType: string;
      clickText: string;
      clickURL: string;
      search: {
        autoSuggestSearchTerm: string;
        searchTerm: string;
        searchFilters: string;
        searchResults: string;
      };
      cardDescription: string;
      accordionAction: string;
      interactionSection: string;
      userRole: string;
    };
    pageInfo: {
      pageName: string;
      pageTitle: string;
      pageType: string;
      pageUrl: string;
      talid: string;
      mcode: string;
      referrer: string;
      language: string;
      primaryCategory: string;
      subCategory1: string;
      subCategory2: string;
      subCategory3: string;
      site: {
        brand: string;
        environment: string;
        domain: string;
      };
    };
    form: {
      formName: string;
      formStep: string;
      formSubStep: string;
      quoteId: string;
      referenceNumber: string;
      formAction: string;
      tpdCover: string;
      traumaCover: string;
      smoker: string;
      state: string;
      postcode: string;
      occupation: string;
      age: string;
      gender: string;
      amount: string;
      income: string;
      lifeCover: string;
      product: string;
      vertical: string;
    };
    user: {
      email: string;
      phoneNumber: string;
      membershipType: string;
      membershipId: string;
      loginstatus: string;
      loginId: string;
      role: string;
    };
    event: string;
  }
```
---

## Examples for Specific Elements

Below are examples of how to implement the `digitalData` object for various elements, along with sample payloads and images.

### 1. Navigation Bar

When a user interacts with the navigation bar, the `digitalData` object should capture relevant details.

**Example Payload:**

```javascript
{
    "interaction": {
        "eventType": "navigation",
        "clickText": "Insurance Products",
        "clickURL": "https://datalayer-test.com",
        "search": {
            "autoSuggestSearchTerm": "",
            "searchTerm": "",
            "searchFilters": "",
            "searchResults": ""
        },
        "cardDescription": "",
        "accordionAction": "",
        "interactionSection": "header",
        "userRole": ""
    },
    "pageInfo": {
        "pageName": "Test Website",
        "pageTitle": "Test Website",
        "pageType": "Insurance Info",
        "pageUrl": "https://datalayer-test.com",
        "talid": "12345",
        "mcode": "insurancePage",
        "referrer": "",
        "language": "en-AU",
        "primaryCategory": "Insurance",
        "subCategory1": "",
        "subCategory2": "",
        "subCategory3": "",
        "site": {
            "brand": "Insurance Corp",
            "environment": "production",
            "domain": "datalayer-test.com"
        }
    },
    "form": {
        "formName": "",
        "formStep": "",
        "formSubStep": "",
        "quoteId": "",
        "referenceNumber": "",
        "formAction": "",
        "tpdCover": "",
        "traumaCover": "",
        "smoker": "",
        "state": "",
        "postcode": "",
        "occupation": "",
        "age": "",
        "gender": "",
        "amount": "",
        "income": "",
        "lifeCover": "",
        "product": "",
        "vertical": ""
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
}
```
**Image Illustration:**

![Navigation Bar Example](./pics/NavBars.png)

---

### 2. Card

For interactions with cards, such as clicking on a product card, details should be captured accordingly.

**Example Payload:**

```javascript
{
    "interaction": {
        "eventType": "card",
        "clickText": "Pet Insurance",
        "clickURL": "https://datalayer-test.com",
        "search": {
            "autoSuggestSearchTerm": "",
            "searchTerm": "",
            "searchFilters": "",
            "searchResults": ""
        },
        "cardDescription": "Protect what matters most with our comprehensive pet insurance",
        "accordionAction": "",
        "interactionSection": "content",
        "userRole": ""
    },
    "pageInfo": {
        "pageName": "Test Website",
        "pageTitle": "Test Website",
        "pageType": "Insurance Info",
        "pageUrl": "https://datalayer-test.com",
        "talid": "12345",
        "mcode": "insurancePage",
        "referrer": "",
        "language": "en-AU",
        "primaryCategory": "Insurance",
        "subCategory1": "",
        "subCategory2": "",
        "subCategory3": "",
        "site": {
            "brand": "Insurance Corp",
            "environment": "production",
            "domain": "datalayer-test.com"
        }
    },
    "form": {
        "formName": "",
        "formStep": "",
        "formSubStep": "",
        "quoteId": "",
        "referenceNumber": "",
        "formAction": "",
        "tpdCover": "",
        "traumaCover": "",
        "smoker": "",
        "state": "",
        "postcode": "",
        "occupation": "",
        "age": "",
        "gender": "",
        "amount": "",
        "income": "",
        "lifeCover": "",
        "product": "",
        "vertical": ""
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
}

```
**Image Illustration:**

![Card Interaction Example](./pics/Cards.png)

---

### 3. Button (CTA)

Capturing interactions with call-to-action buttons is essential for tracking user engagement.

**Example Payload:**

```javascript
{
    "interaction": {
        "eventType": "button",
        "clickText": "Get a Quote Now",
        "clickURL": "https://datalayer-test.com",
        "search": {
            "autoSuggestSearchTerm": "",
            "searchTerm": "",
            "searchFilters": "",
            "searchResults": ""
        },
        "cardDescription": "",
        "accordionAction": "",
        "interactionSection": "content",
        "userRole": ""
    },
    "pageInfo": {
        "pageName": "Test Website",
        "pageTitle": "Test Website",
        "pageType": "Insurance Info",
        "pageUrl": "https://datalayer-test.com",
        "talid": "12345",
        "mcode": "insurancePage",
        "referrer": "",
        "language": "en-AU",
        "primaryCategory": "Insurance",
        "subCategory1": "",
        "subCategory2": "",
        "subCategory3": "",
        "site": {
            "brand": "Insurance Corp",
            "environment": "production",
            "domain": "datalayer-test.com"
        }
    },
    "form": {
        "formName": "",
        "formStep": "",
        "formSubStep": "",
        "quoteId": "",
        "referenceNumber": "",
        "formAction": "",
        "tpdCover": "",
        "traumaCover": "",
        "smoker": "",
        "state": "",
        "postcode": "",
        "occupation": "",
        "age": "",
        "gender": "",
        "amount": "",
        "income": "",
        "lifeCover": "",
        "product": "",
        "vertical": ""
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
}

```
**Image Illustration:**

![Button (CTA) Interaction Example](./pics/button.png)

---

### 4. Accordion

When users interact with accordion elements, such as expanding or collapsing sections, record the actions.

**Example Payload:**

```javascript
{
    "interaction": {
        "eventType": "accordion",
        "clickText": "FAQ: How do I file a claim?",
        "clickURL": "https://datalayer-test.com",
        "search": {
            "autoSuggestSearchTerm": "",
            "searchTerm": "",
            "searchFilters": "",
            "searchResults": ""
        },
        "cardDescription": "",
        "accordionAction": "Open",
        "interactionSection": "content",
        "userRole": ""
    },
    "pageInfo": {
        "pageName": "Test Website",
        "pageTitle": "Test Website",
        "pageType": "Insurance Info",
        "pageUrl": "https://datalayer-test.com",
        "talid": "12345",
        "mcode": "insurancePage",
        "referrer": "",
        "language": "en-AU",
        "primaryCategory": "Insurance",
        "subCategory1": "",
        "subCategory2": "",
        "subCategory3": "",
        "site": {
            "brand": "Insurance Corp",
            "environment": "production",
            "domain": "datalayer-test.aiprojectlabs.com"
        }
    },
    "form": {
        "formName": "",
        "formStep": "",
        "formSubStep": "",
        "quoteId": "",
        "referenceNumber": "",
        "formAction": "",
        "tpdCover": "",
        "traumaCover": "",
        "smoker": "",
        "state": "",
        "postcode": "",
        "occupation": "",
        "age": "",
        "gender": "",
        "amount": "",
        "income": "",
        "lifeCover": "",
        "product": "",
        "vertical": ""
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
}

```
**Image Illustration:**

![Accordion Interaction Example](./pics/Accordion.png)

---

### 5. Search Bar

For interactions with the search bar, including the terms entered and the results, the data captured helps in understanding user intent and improving search functionality.

**Example Payload:**

```javascript
{
    "interaction": {
        "eventType": "search",
        "clickText": "",
        "clickURL": "https://datalayer-tesr.com",
        "search": {
            "autoSuggestSearchTerm": "",
            "searchTerm": "insurance",
            "searchFilters": "",
            "searchResults": ""
        },
        "cardDescription": "",
        "accordionAction": "",
        "interactionSection": "header",
        "userRole": ""
    },
    "pageInfo": {
        "pageName": "Test Website",
        "pageTitle": "Test Website",
        "pageType": "Insurance Info",
        "pageUrl": "https://datalayer-test.com",
        "talid": "12345",
        "mcode": "insurancePage",
        "referrer": "",
        "language": "en-AU",
        "primaryCategory": "Insurance",
        "subCategory1": "",
        "subCategory2": "",
        "subCategory3": "",
        "site": {
            "brand": "Insurance Corp",
            "environment": "production",
            "domain": "datalayer-test.com"
        }
    },
    "form": {
        "formName": "",
        "formStep": "",
        "formSubStep": "",
        "quoteId": "",
        "referenceNumber": "",
        "formAction": "",
        "tpdCover": "",
        "traumaCover": "",
        "smoker": "",
        "state": "",
        "postcode": "",
        "occupation": "",
        "age": "",
        "gender": "",
        "amount": "",
        "income": "",
        "lifeCover": "",
        "product": "",
        "vertical": ""
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
}
```
**Image Illustration:**

![Search Bar Interaction Example](./pics/search.png)

---

### 5. Form Submission

For interactions with the forms, this will populate the object form with its proeprty values, depending on the step. This will mean there will be a new datalayer push for every new step in the form the user is in

**Example Payload:**

```javascript
{
    "interaction": {
        "eventType": "button",
        "clickText": "",
        "clickURL": "https://datalayer-tesr.com",
        "search": {
            "autoSuggestSearchTerm": "",
            "searchTerm": "insurance",
            "searchFilters": "",
            "searchResults": ""
        },
        "cardDescription": "",
        "accordionAction": "",
        "interactionSection": "header",
        "userRole": ""
    },
    "pageInfo": {
        "pageName": "Test Website",
        "pageTitle": "Test Website",
        "pageType": "Insurance Info",
        "pageUrl": "https://datalayer-test.com",
        "talid": "12345",
        "mcode": "insurancePage",
        "referrer": "",
        "language": "en-AU",
        "primaryCategory": "Insurance",
        "subCategory1": "",
        "subCategory2": "",
        "subCategory3": "",
        "site": {
            "brand": "Insurance Corp",
            "environment": "production",
            "domain": "datalayer-test.com"
        }
    },
    "form": {
        "formName": "life-insurance-form",
        "formStep": "form start",
        "formSubStep": "",
        "quoteId": "123456",
        "referenceNumber": "78910",
        "formAction": "",
        "tpdCover": "",
        "traumaCover": "",
        "smoker": "yes",
        "state": "nsw",
        "postcode": "2200",
        "occupation": "senior data analyst",
        "age": "18",
        "gender": "male",
        "amount": "1000000",
        "income": "100",
        "lifeCover": "20",
        "product": "life-insurance",
        "vertical": ""
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
}
```
**Image Illustration:**

![Search Bar Interaction Example](./pics/search.png)

---

## The `digitalData` Object Structure for event `page view`


Below is the structure of the `digitalData` object that needs to be deployed. This example is for a page load for an authenticated user:


```javascript
digitalData.push({
"pageInfo": {
  "pageName": "DataLayer Test Home",
  "pageTitle": "DataLayer Test - Home",
  "pageType": "homepage",
  "pageUrl": "https://datalayer-test.com",
  "talid": "TL-0012345",
  "mcode": "MC-67890",
  "referrer": "",
  "language": "en-AU",
  "primaryCategory": "Data Analytics",
  "subCategory1": "Tracking",
  "subCategory2": "Data Layer Implementation",
  "subCategory3": "",
  "site": {
    "brand": "DataLayer Test",
    "environment": "production",
    "domain": "datalayer-test.com"
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
    "email": "e9f6a7c0-3b2f-4d5e-9a1b-7c8d9e0f1234",
    "phoneNumber": "041111111",
    "membershipType": "broker",
    "membershipId": "123456",
    "loginstatus": "yes",
    "loginId": "645345",
    "role": ""
  },
  "event": "pageView"
});
```


## Notes

- **Consistency**: Ensure all data pushed to the `digitalData` object is accurate and consistently formatted.
- **Placeholder Values**: Replace placeholder values (e.g., empty strings, comments) with actual data relevant to the user's interaction and the page context.


