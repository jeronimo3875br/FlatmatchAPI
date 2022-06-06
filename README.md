# Property payment data

Routes for handling property payment data.

# Routes

Below is all the routes registered in this document and ready for use

```bash

  # Filter property by specific parameter
  GET /api/properties/find-payment

  # Update property payment details
  PUT /api/properties/change-payment-status/:id

```

## GET /api/properties/find-payment

This route responsible for filtering a property by parameter and specific value, receives 2 attributes passed via query, namely:

```yaml

  query:
  
    by: 
      type: "String"
      description: "Specific filter that will be used in the property query."
      acceptable: 
        PROPERTY_ID: 
          description: "Specific property ID."
          
        PAYMENT_STATUS: 
          description: "Payment status for that property."
          
        PAYMENT_METHOD: 
          type: "String",
          description: "Payment method used in this property."
          
        PAYMENT_PLAN: 
          description: "Payment plan used in this property."
          
        PAYMENT_PRICE: 
          description: "Price paid for listing this property."

    value:
      type: "String"
      description: "Value that will be filtered in the property query."
    
```

Request example:

```

  GET /api/properties/find-payment?by=PAYMENT_METHOD&value=CARD

```

## PUT /api/properties/change-payment-status/:id

Route responsible for changing payment data for a specific property. This rora receives a parameter and accepts values passed via json, these values are the property data that can be updated.

```yaml

  param: 
    id:
      type: "String"
      description: "Specific property ID."
      
  body: 
    price: 
      type: "String"
      description: "Price paid for the ad."
      
    method: 
      type: "String"
      description: "Payment method used."
      acceptable: 
        PIX: 
          description: "Payment method PIX."
          
        BOLETO: 
          description: "Payment method BOLETO."
          
        CARD: 
          description: "Payment method CREDIT CARD."
      
    status: 
      type: "String"
      description: "Payment status for this property.",
      acceptable:
        PAID: 
          description: "Payment made."
          
        WAITING: 
          description: "Awaiting payment."
          
        CANCELED: 
          description: "Payment cancelled."
          
        INACTIVE: 
          description: "Inactive payment."
      
    plan: 
      type: "String"
      description: "Plan used to advertise the property."
      acceptable: 
        PEOPLE:
          description: "Payment made by an individual."
          
        COMPANY: 
          description: "Payment made by a company."
      
    adverstising: 
      type: "String"
      description: "Ad status."
      acceptable:
        ACTIVE: 
          type: "String",
          description: "Active ad."
          
        INACTIVE:
          type: "String"
          description: "Inactive ad."

```

Request example:

```

  PUT /api/properties/change-payment-status/259249c245m92929m
  
```

Data to be updated and its values in json:

```json

{
    "method": "CARD",
    "plan": "COMPANY",
    "status": "PAID",
    "price": 48.00
}

```
