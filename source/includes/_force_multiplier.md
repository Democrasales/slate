# Force Multiplier API

<aside class="notice">This section is dedicated to Force Multiplier API endpoints.</aside>

## Bootstrap Database

If using the API locally, seed your database with the questionnaire content:

<code>
$> rake db:seed:questionnaire
</code>

## Lead Statuses

A lead has a <b>lead status</b> and a <b>questionnaire status</b>, each of which may change every time a lead is updated, depending on the state of other lead attributes.

Status | Values
---------- | -------
lead_status | follow_up, qualified, disqualified
questionnaire_status | unstarted, started, completed

## New Lead

This endpoint instantiates a lead.

### HTTP Request

<code>GET http://democrasales.com/api/v1/leads/new</code>

> A new lead looks like this:

```shell
{
  "id": null,
  "salesperson_id": null,
  "marketer_id": null,
  "customer_id": null,
  "address_id": null,
  "first_name": null,
  "last_name": null,
  "business_name": null,
  "phone": null,
  "email": null,
  "lead_status": "follow_up",
  "questionnaire_status": "unstarted",
  "questionnaire_answers": [],
  "notes": null,
  "follow_up_date": null,
  "visit_date": null,
  "created_at": null,
  "questionnaire": {
    "id": 3,
    "name": "Health & Medical",
    "questions": [
      {
        "id": 19,
        "type": "MultipleChoiceQuestion",
        "content": "If we can help you save money and provide superior customer service and support, would you be interested in being visited by one of our account managers who can provide you with a proposal?",
        "position": 1,
        "required": true,
        "has_questions": false,
        "next_question_id": 20,
        "prev_question_id": null,
        "question_options": [
          {
            "id": 73,
            "input": "radio",
            "data_type": "boolean",
            "label": "Yes",
            "name": "yes",
            "position": 1
          },
          {
            "id": 74,
            "input": "radio",
            "data_type": "boolean",
            "label": "No",
            "name": "no",
            "position": 2
          }
        ]
      },
      {
        "id": 20,
        "type": "MultipleSelectQuestion",
        "content": "How do you place orders?",
        "position": 2,
        "required": true,
        "has_questions": false,
        "next_question_id": 21,
        "prev_question_id": 19,
        "question_options": [
          {
            "id": 75,
            "input": "radio",
            "data_type": "boolean",
            "label": "Online",
            "name": "online",
            "position": 1
          },
          {
            "id": 76,
            "input": "radio",
            "data_type": "boolean",
            "label": "Phone",
            "name": "phone",
            "position": 2
          },
          {
            "id": 77,
            "input": "radio",
            "data_type": "boolean",
            "label": "Fax",
            "name": "fax",
            "position": 3
          },
          {
            "id": 78,
            "input": "radio",
            "data_type": "boolean",
            "label": "E-mail",
            "name": "email",
            "position": 4
          },
          {
            "id": 79,
            "input": "text",
            "data_type": "string",
            "label": "Other",
            "name": "other",
            "position": 5
          },
          {
            "id": 80,
            "input": "radio",
            "data_type": "boolean",
            "label": "No Answer",
            "name": "no_answer",
            "position": 6
          }
        ]
      },
      {
        "id": 21,
        "type": "MultipleChoiceQuestion",
        "content": "Do you know if you are currently affiliated with any Group Purchasing Organization?",
        "position": 3,
        "required": true,
        "has_questions": true,
        "next_question_id": 23,
        "prev_question_id": 20,
        "questions": [
          {
            "id": 22,
            "type": "MultipleSelectQuestion",
            "content": "With which GPO are you affiliated?",
            "position": 1,
            "required": true,
            "has_questions": false,
            "next_question_id": null,
            "prev_question_id": null
          }
        ],
        "question_options": [
          {
            "id": 81,
            "input": "radio",
            "data_type": "boolean",
            "label": "Yes",
            "name": "yes",
            "position": 1
          },
          {
            "id": 82,
            "input": "radio",
            "data_type": "boolean",
            "label": "No",
            "name": "no",
            "position": 2
          },
          {
            "id": 83,
            "input": "radio",
            "data_type": "boolean",
            "label": "No Answer",
            "name": "no_answer",
            "position": 3
          }
        ]
      },
      {
        "id": 23,
        "type": "MultipleChoiceQuestion",
        "content": "Would you be interested in purchasing high-quality, brand-name products you are familiar with at prices that are the same or better than your current distributor's private label brand?",
        "position": 4,
        "required": true,
        "has_questions": false,
        "next_question_id": 24,
        "prev_question_id": 21,
        "question_options": [
          {
            "id": 90,
            "input": "radio",
            "data_type": "boolean",
            "label": "Yes",
            "name": "yes",
            "position": 1
          },
          {
            "id": 91,
            "input": "radio",
            "data_type": "boolean",
            "label": "No",
            "name": "no",
            "position": 2
          },
          {
            "id": 92,
            "input": "radio",
            "data_type": "boolean",
            "label": "No Answer",
            "name": "no_answer",
            "position": 3
          }
        ]
      },
      {
        "id": 24,
        "type": "MultipleSelectQuestion",
        "content": "Rank the following concerns that you have with your current distribution (scale of 1-10 with 1 meaning not a concern at all and 10 being a major concern).",
        "position": 5,
        "required": true,
        "has_questions": false,
        "next_question_id": 25,
        "prev_question_id": 23,
        "question_options": [
          {
            "id": 93,
            "input": "range",
            "data_type": "integer",
            "label": "Pricing",
            "name": "pricing",
            "position": 1
          },
          {
            "id": 94,
            "input": "range",
            "data_type": "integer",
            "label": "Product Availability/Backorders",
            "name": "availability",
            "position": 2
          },
          {
            "id": 95,
            "input": "range",
            "data_type": "integer",
            "label": "Product Quality",
            "name": "quality",
            "position": 3
          },
          {
            "id": 96,
            "input": "range",
            "data_type": "integer",
            "label": "Customer Service",
            "name": "service",
            "position": 4
          },
          {
            "id": 97,
            "input": "range",
            "data_type": "integer",
            "label": "Accessibility/Availability of your account manager",
            "name": "manager",
            "position": 5
          },
          {
            "id": 98,
            "input": "range",
            "data_type": "integer",
            "label": "Equipment repair and availability of loaner equipment",
            "name": "equipment",
            "position": 6
          },
          {
            "id": 99,
            "input": "range",
            "data_type": "integer",
            "label": "Accounting (invoicing, statements, credits and returns)",
            "name": "accounting",
            "position": 7
          },
          {
            "id": 100,
            "input": "range",
            "data_type": "integer",
            "label": "Ease of Ordering",
            "name": "ordering",
            "position": 8
          },
          {
            "id": 101,
            "input": "range",
            "data_type": "integer",
            "label": "Pricing",
            "name": "pricing",
            "position": 9
          }
        ]
      },
      {
        "id": 25,
        "type": "MultipleSelectQuestion",
        "content": "From which distributor are you currently buying medical supplies?",
        "position": 6,
        "required": true,
        "has_questions": false,
        "next_question_id": 26,
        "prev_question_id": 24,
        "question_options": [
          {
            "id": 102,
            "input": "radio",
            "data_type": "boolean",
            "label": "McKesson",
            "name": "mckesson",
            "position": 1
          },
          {
            "id": 103,
            "input": "radio",
            "data_type": "boolean",
            "label": "Henry Schein",
            "name": "henry_schein",
            "position": 2
          },
          {
            "id": 104,
            "input": "radio",
            "data_type": "boolean",
            "label": "Medline",
            "name": "medline",
            "position": 3
          },
          {
            "id": 105,
            "input": "text",
            "data_type": "string",
            "label": "Other",
            "name": "other",
            "position": 4
          },
          {
            "id": 106,
            "input": "radio",
            "data_type": "boolean",
            "label": "No Answer",
            "name": "no_answer",
            "position": 5
          }
        ]
      },
      {
        "id": 26,
        "type": "FreeTextQuestion",
        "content": "Is there anything else that I haven't covered that you feel is important when evaluating or selecting a supplier?",
        "position": 7,
        "required": false,
        "has_questions": false,
        "next_question_id": 27,
        "prev_question_id": 25,
        "question_options": [
          {
            "id": 107,
            "input": "textarea",
            "data_type": "string",
            "label": null,
            "name": "evaluating_supplier",
            "position": 1
          }
        ]
      },
      {
        "id": 27,
        "type": "FreeTextQuestion",
        "content": "If you could change one thing about your current supplier what would it be and why?",
        "position": 8,
        "required": false,
        "has_questions": false,
        "next_question_id": null,
        "prev_question_id": 26,
        "question_options": [
          {
            "id": 108,
            "input": "textarea",
            "data_type": "string",
            "label": null,
            "name": "change_supplier",
            "position": 1
          }
        ]
      }
    ]
  }
}
```

## Get Lead

This endpoint retrieves an existing lead.

### HTTP Request

<code>GET http://democrasales.com/api/v1/leads/:id</code>

> An existing lead looks like this:

```shell
{
  "customer": {
    "id": 1,
    "categories": [{
      "title": "Bars",
      "alias": "bars"
    }],
    "coordinates": {
      "latitude": 40.7143528,
      "longitude": -74.0059731
    },
    "name": "Mourad Restaurant",
    "phone": "+14156602500",
    "display_phone": "+14156602500",
    "photos": ["https://s3-media2.fl.yelpcdn.com/bphoto/wlbRTdS4LXvR1vR4sVwirA/o.jpg", "https://s3-media4.fl.yelpcdn.com/bphoto/ULuBpYRQcRHpNOWGgfNaQA/o.jpg", "https://s3-media2.fl.yelpcdn.com/bphoto/aagkD5lUHBxvZ9-9JJ-AeQ/o.jpg"],
    "url": "https://www.yelp.com/biz/mourad-restaurant-san-francisco?adjust_creative=jMxsvyOFUo07wr15E7Y1Egu0026utm_campaign=yelp_api_v3u0026utm_medium=api_v3_business_lookupu0026utm_source=jMxsvyOFUo07wr15E7Y1Eg",
    "hours": [{
      "open": [{
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 0
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 1
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 2
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 3
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 4
      }, {
        "is_overnight": false,
        "start": "1700",
        "end": "2200",
        "day": 5
      }, {
        "is_overnight": false,
        "start": "1700",
        "end": "2200",
        "day": 6
      }],
      "hours_type": "REGULAR",
      "is_open_now": false
    }],
    "yelp_id": "mourad-restaurant-san-francisco",
    "location": {
      "display_address": ["2224 South Colorado Street", "Philadelphia, PA 19145"],
      "address1": "2224 South Colorado Street",
      "city": "Philadelphia",
      "state": "PA",
      "country": "US",
      "zip_code": "19145"
    },
    "lead": {
      "id": 1,
      "salesperson_id": 2,
      "marketer_id": 3,
      "customer_id": 4,
      "address_id": 5,
      "first_name": "John",
      "last_name": "Doe",
      "business_name": "Mourad Restaurant",
      "phone": "123 456 7890",
      "email": "owner@mourad.com",
      "lead_status": "follow_up",
      "questionnaire_status": "unstarted",
      "questionnaire_answers": [
        {
          "id": 15,
          "question_id": 1,
          "question_option_id": 4,
          "value": '6'
        },
        {
          "id": 16,
          "question_id": 1,
          "question_option_id": 6,
          "value": '2'
        }
      ],
      "notes": "Will call back when owner is available",
      "follow_up_date": "2018-08-16 12:40:25 -0400",
      "visit_date": "2018-07-16 12:40:25 -0400",
      "created_at": "2018-07-16 12:40:25 -0400",
      "questionnaire": {
        "id": 3,
        "name": "Health & Medical",
        "questions": [{
            "id": 19,
            "type": "MultipleChoiceQuestion",
            "content": "If we can help you save money and provide superior customer service and support, would you be interested in being visited by one of our account managers who can provide you with a proposal?",
            "position": 1,
            "required": true,
            "has_questions": false,
            "next_question_id": 20,
            "prev_question_id": null,
            "question_options": [{
                "id": 73,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 74,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              }
            ]
          },
          {
            "id": 20,
            "type": "MultipleSelectQuestion",
            "content": "How do you place orders?",
            "position": 2,
            "required": true,
            "has_questions": false,
            "next_question_id": 21,
            "prev_question_id": 19,
            "question_options": [{
                "id": 75,
                "input": "radio",
                "data_type": "boolean",
                "label": "Online",
                "name": "online",
                "position": 1
              },
              {
                "id": 76,
                "input": "radio",
                "data_type": "boolean",
                "label": "Phone",
                "name": "phone",
                "position": 2
              },
              {
                "id": 77,
                "input": "radio",
                "data_type": "boolean",
                "label": "Fax",
                "name": "fax",
                "position": 3
              },
              {
                "id": 78,
                "input": "radio",
                "data_type": "boolean",
                "label": "E-mail",
                "name": "email",
                "position": 4
              },
              {
                "id": 79,
                "input": "text",
                "data_type": "string",
                "label": "Other",
                "name": "other",
                "position": 5
              },
              {
                "id": 80,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 6
              }
            ]
          },
          {
            "id": 21,
            "type": "MultipleChoiceQuestion",
            "content": "Do you know if you are currently affiliated with any Group Purchasing Organization?",
            "position": 3,
            "required": true,
            "has_questions": true,
            "next_question_id": 23,
            "prev_question_id": 20,
            "questions": [{
              "id": 22,
              "type": "MultipleSelectQuestion",
              "content": "With which GPO are you affiliated?",
              "position": 1,
              "required": true,
              "has_questions": false,
              "next_question_id": null,
              "prev_question_id": null
            }],
            "question_options": [{
                "id": 81,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 82,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              },
              {
                "id": 83,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 3
              }
            ]
          },
          {
            "id": 23,
            "type": "MultipleChoiceQuestion",
            "content": "Would you be interested in purchasing high-quality, brand-name products you are familiar with at prices that are the same or better than your current distributor's private label brand?",
            "position": 4,
            "required": true,
            "has_questions": false,
            "next_question_id": 24,
            "prev_question_id": 21,
            "question_options": [{
                "id": 90,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 91,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              },
              {
                "id": 92,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 3
              }
            ]
          },
          {
            "id": 24,
            "type": "MultipleSelectQuestion",
            "content": "Rank the following concerns that you have with your current distribution (scale of 1-10 with 1 meaning not a concern at all and 10 being a major concern).",
            "position": 5,
            "required": true,
            "has_questions": false,
            "next_question_id": 25,
            "prev_question_id": 23,
            "question_options": [{
                "id": 93,
                "input": "range",
                "data_type": "integer",
                "label": "Pricing",
                "name": "pricing",
                "position": 1
              },
              {
                "id": 94,
                "input": "range",
                "data_type": "integer",
                "label": "Product Availability/Backorders",
                "name": "availability",
                "position": 2
              },
              {
                "id": 95,
                "input": "range",
                "data_type": "integer",
                "label": "Product Quality",
                "name": "quality",
                "position": 3
              },
              {
                "id": 96,
                "input": "range",
                "data_type": "integer",
                "label": "Customer Service",
                "name": "service",
                "position": 4
              },
              {
                "id": 97,
                "input": "range",
                "data_type": "integer",
                "label": "Accessibility/Availability of your account manager",
                "name": "manager",
                "position": 5
              },
              {
                "id": 98,
                "input": "range",
                "data_type": "integer",
                "label": "Equipment repair and availability of loaner equipment",
                "name": "equipment",
                "position": 6
              },
              {
                "id": 99,
                "input": "range",
                "data_type": "integer",
                "label": "Accounting (invoicing, statements, credits and returns)",
                "name": "accounting",
                "position": 7
              },
              {
                "id": 100,
                "input": "range",
                "data_type": "integer",
                "label": "Ease of Ordering",
                "name": "ordering",
                "position": 8
              },
              {
                "id": 101,
                "input": "range",
                "data_type": "integer",
                "label": "Pricing",
                "name": "pricing",
                "position": 9
              }
            ]
          },
          {
            "id": 25,
            "type": "MultipleSelectQuestion",
            "content": "From which distributor are you currently buying medical supplies?",
            "position": 6,
            "required": true,
            "has_questions": false,
            "next_question_id": 26,
            "prev_question_id": 24,
            "question_options": [{
                "id": 102,
                "input": "radio",
                "data_type": "boolean",
                "label": "McKesson",
                "name": "mckesson",
                "position": 1
              },
              {
                "id": 103,
                "input": "radio",
                "data_type": "boolean",
                "label": "Henry Schein",
                "name": "henry_schein",
                "position": 2
              },
              {
                "id": 104,
                "input": "radio",
                "data_type": "boolean",
                "label": "Medline",
                "name": "medline",
                "position": 3
              },
              {
                "id": 105,
                "input": "text",
                "data_type": "string",
                "label": "Other",
                "name": "other",
                "position": 4
              },
              {
                "id": 106,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 5
              }
            ]
          },
          {
            "id": 26,
            "type": "FreeTextQuestion",
            "content": "Is there anything else that I haven't covered that you feel is important when evaluating or selecting a supplier?",
            "position": 7,
            "required": false,
            "has_questions": false,
            "next_question_id": 27,
            "prev_question_id": 25,
            "question_options": [{
              "id": 107,
              "input": "textarea",
              "data_type": "string",
              "label": null,
              "name": "evaluating_supplier",
              "position": 1
            }]
          },
          {
            "id": 27,
            "type": "FreeTextQuestion",
            "content": "If you could change one thing about your current supplier what would it be and why?",
            "position": 8,
            "required": false,
            "has_questions": false,
            "next_question_id": null,
            "prev_question_id": 26,
            "question_options": [{
              "id": 108,
              "input": "textarea",
              "data_type": "string",
              "label": null,
              "name": "change_supplier",
              "position": 1
            }]
          }
        ]
      }
    }
  }
```

## Create Lead

This endpoint creates a lead.

### HTTP Request

<code>POST http://democrasales.com/api/v1/leads</code>

### Query Parameters

Parameter | Required | Description
----------| ------- | -----------
yelp_id | required | Yelp ID of business
first_name | required | Business contact's first name
last_name | required | Business contact's last name
phone | required | Business contact's phone number
email | optional | Business contact's e-mail address
follow_up_date | required, if lead_status = 'follow_up' | Date to send follow up email
notes | optional | Marketer's lead notes

> The response looks like this:

```shell
{
  "customer": {
    "id": 1,
    "categories": [{
      "title": "Bars",
      "alias": "bars"
    }],
    "coordinates": {
      "latitude": 40.7143528,
      "longitude": -74.0059731
    },
    "name": "Mourad Restaurant",
    "phone": "+14156602500",
    "display_phone": "+14156602500",
    "photos": ["https://s3-media2.fl.yelpcdn.com/bphoto/wlbRTdS4LXvR1vR4sVwirA/o.jpg", "https://s3-media4.fl.yelpcdn.com/bphoto/ULuBpYRQcRHpNOWGgfNaQA/o.jpg", "https://s3-media2.fl.yelpcdn.com/bphoto/aagkD5lUHBxvZ9-9JJ-AeQ/o.jpg"],
    "url": "https://www.yelp.com/biz/mourad-restaurant-san-francisco?adjust_creative=jMxsvyOFUo07wr15E7Y1Egu0026utm_campaign=yelp_api_v3u0026utm_medium=api_v3_business_lookupu0026utm_source=jMxsvyOFUo07wr15E7Y1Eg",
    "hours": [{
      "open": [{
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 0
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 1
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 2
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 3
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 4
      }, {
        "is_overnight": false,
        "start": "1700",
        "end": "2200",
        "day": 5
      }, {
        "is_overnight": false,
        "start": "1700",
        "end": "2200",
        "day": 6
      }],
      "hours_type": "REGULAR",
      "is_open_now": false
    }],
    "yelp_id": "mourad-restaurant-san-francisco",
    "location": {
      "display_address": ["2224 South Colorado Street", "Philadelphia, PA 19145"],
      "address1": "2224 South Colorado Street",
      "city": "Philadelphia",
      "state": "PA",
      "country": "US",
      "zip_code": "19145"
    },
    "lead": {
      "id": 1,
      "salesperson_id": 2,
      "marketer_id": 3,
      "customer_id": 4,
      "address_id": 5,
      "first_name": "John",
      "last_name": "Doe",
      "business_name": "Mourad Restaurant",
      "phone": "123 456 7890",
      "email": "owner@mourad.com",
      "lead_status": "follow_up",
      "questionnaire_status": "unstarted",
      "questionnaire_answers": [
        {
          "id": 15,
          "question_id": 1,
          "question_option_id": 4,
          "value": '6'
        },
        {
          "id": 16,
          "question_id": 1,
          "question_option_id": 6,
          "value": '2'
        }
      ],
      "notes": "Will call back when owner is available",
      "follow_up_date": "2018-08-16 12:40:25 -0400",
      "visit_date": "2018-07-16 12:40:25 -0400",
      "created_at": "2018-07-16 12:40:25 -0400",
      "questionnaire": {
        "id": 3,
        "name": "Health & Medical",
        "questions": [{
            "id": 19,
            "type": "MultipleChoiceQuestion",
            "content": "If we can help you save money and provide superior customer service and support, would you be interested in being visited by one of our account managers who can provide you with a proposal?",
            "position": 1,
            "required": true,
            "has_questions": false,
            "next_question_id": 20,
            "prev_question_id": null,
            "question_options": [{
                "id": 73,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 74,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              }
            ]
          },
          {
            "id": 20,
            "type": "MultipleSelectQuestion",
            "content": "How do you place orders?",
            "position": 2,
            "required": true,
            "has_questions": false,
            "next_question_id": 21,
            "prev_question_id": 19,
            "question_options": [{
                "id": 75,
                "input": "radio",
                "data_type": "boolean",
                "label": "Online",
                "name": "online",
                "position": 1
              },
              {
                "id": 76,
                "input": "radio",
                "data_type": "boolean",
                "label": "Phone",
                "name": "phone",
                "position": 2
              },
              {
                "id": 77,
                "input": "radio",
                "data_type": "boolean",
                "label": "Fax",
                "name": "fax",
                "position": 3
              },
              {
                "id": 78,
                "input": "radio",
                "data_type": "boolean",
                "label": "E-mail",
                "name": "email",
                "position": 4
              },
              {
                "id": 79,
                "input": "text",
                "data_type": "string",
                "label": "Other",
                "name": "other",
                "position": 5
              },
              {
                "id": 80,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 6
              }
            ]
          },
          {
            "id": 21,
            "type": "MultipleChoiceQuestion",
            "content": "Do you know if you are currently affiliated with any Group Purchasing Organization?",
            "position": 3,
            "required": true,
            "has_questions": true,
            "next_question_id": 23,
            "prev_question_id": 20,
            "questions": [{
              "id": 22,
              "type": "MultipleSelectQuestion",
              "content": "With which GPO are you affiliated?",
              "position": 1,
              "required": true,
              "has_questions": false,
              "next_question_id": null,
              "prev_question_id": null
            }],
            "question_options": [{
                "id": 81,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 82,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              },
              {
                "id": 83,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 3
              }
            ]
          },
          {
            "id": 23,
            "type": "MultipleChoiceQuestion",
            "content": "Would you be interested in purchasing high-quality, brand-name products you are familiar with at prices that are the same or better than your current distributor's private label brand?",
            "position": 4,
            "required": true,
            "has_questions": false,
            "next_question_id": 24,
            "prev_question_id": 21,
            "question_options": [{
                "id": 90,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 91,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              },
              {
                "id": 92,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 3
              }
            ]
          },
          {
            "id": 24,
            "type": "MultipleSelectQuestion",
            "content": "Rank the following concerns that you have with your current distribution (scale of 1-10 with 1 meaning not a concern at all and 10 being a major concern).",
            "position": 5,
            "required": true,
            "has_questions": false,
            "next_question_id": 25,
            "prev_question_id": 23,
            "question_options": [{
                "id": 93,
                "input": "range",
                "data_type": "integer",
                "label": "Pricing",
                "name": "pricing",
                "position": 1
              },
              {
                "id": 94,
                "input": "range",
                "data_type": "integer",
                "label": "Product Availability/Backorders",
                "name": "availability",
                "position": 2
              },
              {
                "id": 95,
                "input": "range",
                "data_type": "integer",
                "label": "Product Quality",
                "name": "quality",
                "position": 3
              },
              {
                "id": 96,
                "input": "range",
                "data_type": "integer",
                "label": "Customer Service",
                "name": "service",
                "position": 4
              },
              {
                "id": 97,
                "input": "range",
                "data_type": "integer",
                "label": "Accessibility/Availability of your account manager",
                "name": "manager",
                "position": 5
              },
              {
                "id": 98,
                "input": "range",
                "data_type": "integer",
                "label": "Equipment repair and availability of loaner equipment",
                "name": "equipment",
                "position": 6
              },
              {
                "id": 99,
                "input": "range",
                "data_type": "integer",
                "label": "Accounting (invoicing, statements, credits and returns)",
                "name": "accounting",
                "position": 7
              },
              {
                "id": 100,
                "input": "range",
                "data_type": "integer",
                "label": "Ease of Ordering",
                "name": "ordering",
                "position": 8
              },
              {
                "id": 101,
                "input": "range",
                "data_type": "integer",
                "label": "Pricing",
                "name": "pricing",
                "position": 9
              }
            ]
          },
          {
            "id": 25,
            "type": "MultipleSelectQuestion",
            "content": "From which distributor are you currently buying medical supplies?",
            "position": 6,
            "required": true,
            "has_questions": false,
            "next_question_id": 26,
            "prev_question_id": 24,
            "question_options": [{
                "id": 102,
                "input": "radio",
                "data_type": "boolean",
                "label": "McKesson",
                "name": "mckesson",
                "position": 1
              },
              {
                "id": 103,
                "input": "radio",
                "data_type": "boolean",
                "label": "Henry Schein",
                "name": "henry_schein",
                "position": 2
              },
              {
                "id": 104,
                "input": "radio",
                "data_type": "boolean",
                "label": "Medline",
                "name": "medline",
                "position": 3
              },
              {
                "id": 105,
                "input": "text",
                "data_type": "string",
                "label": "Other",
                "name": "other",
                "position": 4
              },
              {
                "id": 106,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 5
              }
            ]
          },
          {
            "id": 26,
            "type": "FreeTextQuestion",
            "content": "Is there anything else that I haven't covered that you feel is important when evaluating or selecting a supplier?",
            "position": 7,
            "required": false,
            "has_questions": false,
            "next_question_id": 27,
            "prev_question_id": 25,
            "question_options": [{
              "id": 107,
              "input": "textarea",
              "data_type": "string",
              "label": null,
              "name": "evaluating_supplier",
              "position": 1
            }]
          },
          {
            "id": 27,
            "type": "FreeTextQuestion",
            "content": "If you could change one thing about your current supplier what would it be and why?",
            "position": 8,
            "required": false,
            "has_questions": false,
            "next_question_id": null,
            "prev_question_id": 26,
            "question_options": [{
              "id": 108,
              "input": "textarea",
              "data_type": "string",
              "label": null,
              "name": "change_supplier",
              "position": 1
            }]
          }
        ]
      }
    }
  }
```

## Update Lead

This endpoint updates a specific lead.

### HTTP Request

<code>PUT http://democrasales.com/api/v1/leads/:id</code>

Parameter | Required | Description
----------| ------- | -----------
id | required | Lead ID
first_name | required | Business contact's first name
last_name | required | Business contact's last name
phone | required | Business contact's phone number
email | optional | Business contact's e-mail address
follow_up_date | required, if lead_status = 'follow_up' | Date to send follow up email
notes | optional | Marketer's lead notes

> The response looks like this:

```shell
{
  "customer": {
    "id": 1,
    "categories": [{
      "title": "Bars",
      "alias": "bars"
    }],
    "coordinates": {
      "latitude": 40.7143528,
      "longitude": -74.0059731
    },
    "name": "Mourad Restaurant",
    "phone": "+14156602500",
    "display_phone": "+14156602500",
    "photos": ["https://s3-media2.fl.yelpcdn.com/bphoto/wlbRTdS4LXvR1vR4sVwirA/o.jpg", "https://s3-media4.fl.yelpcdn.com/bphoto/ULuBpYRQcRHpNOWGgfNaQA/o.jpg", "https://s3-media2.fl.yelpcdn.com/bphoto/aagkD5lUHBxvZ9-9JJ-AeQ/o.jpg"],
    "url": "https://www.yelp.com/biz/mourad-restaurant-san-francisco?adjust_creative=jMxsvyOFUo07wr15E7Y1Egu0026utm_campaign=yelp_api_v3u0026utm_medium=api_v3_business_lookupu0026utm_source=jMxsvyOFUo07wr15E7Y1Eg",
    "hours": [{
      "open": [{
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 0
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 1
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 2
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 3
      }, {
        "is_overnight": false,
        "start": "1130",
        "end": "2200",
        "day": 4
      }, {
        "is_overnight": false,
        "start": "1700",
        "end": "2200",
        "day": 5
      }, {
        "is_overnight": false,
        "start": "1700",
        "end": "2200",
        "day": 6
      }],
      "hours_type": "REGULAR",
      "is_open_now": false
    }],
    "yelp_id": "mourad-restaurant-san-francisco",
    "location": {
      "display_address": ["2224 South Colorado Street", "Philadelphia, PA 19145"],
      "address1": "2224 South Colorado Street",
      "city": "Philadelphia",
      "state": "PA",
      "country": "US",
      "zip_code": "19145"
    },
    "lead": {
      "id": 1,
      "salesperson_id": 2,
      "marketer_id": 3,
      "customer_id": 4,
      "address_id": 5,
      "first_name": "John",
      "last_name": "Doe",
      "business_name": "Mourad Restaurant",
      "phone": "123 456 7890",
      "email": "owner@mourad.com",
      "lead_status": "follow_up",
      "questionnaire_status": "unstarted",
      "questionnaire_answers": [
        {
          "id": 15,
          "question_id": 1,
          "question_option_id": 4,
          "value": '6'
        },
        {
          "id": 16,
          "question_id": 1,
          "question_option_id": 6,
          "value": '2'
        }
      ],
      "notes": "Will call back when owner is available",
      "follow_up_date": "2018-08-16 12:40:25 -0400",
      "visit_date": "2018-07-16 12:40:25 -0400",
      "created_at": "2018-07-16 12:40:25 -0400",
      "questionnaire": {
        "id": 3,
        "name": "Health & Medical",
        "questions": [{
            "id": 19,
            "type": "MultipleChoiceQuestion",
            "content": "If we can help you save money and provide superior customer service and support, would you be interested in being visited by one of our account managers who can provide you with a proposal?",
            "position": 1,
            "required": true,
            "has_questions": false,
            "next_question_id": 20,
            "prev_question_id": null,
            "question_options": [{
                "id": 73,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 74,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              }
            ]
          },
          {
            "id": 20,
            "type": "MultipleSelectQuestion",
            "content": "How do you place orders?",
            "position": 2,
            "required": true,
            "has_questions": false,
            "next_question_id": 21,
            "prev_question_id": 19,
            "question_options": [{
                "id": 75,
                "input": "radio",
                "data_type": "boolean",
                "label": "Online",
                "name": "online",
                "position": 1
              },
              {
                "id": 76,
                "input": "radio",
                "data_type": "boolean",
                "label": "Phone",
                "name": "phone",
                "position": 2
              },
              {
                "id": 77,
                "input": "radio",
                "data_type": "boolean",
                "label": "Fax",
                "name": "fax",
                "position": 3
              },
              {
                "id": 78,
                "input": "radio",
                "data_type": "boolean",
                "label": "E-mail",
                "name": "email",
                "position": 4
              },
              {
                "id": 79,
                "input": "text",
                "data_type": "string",
                "label": "Other",
                "name": "other",
                "position": 5
              },
              {
                "id": 80,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 6
              }
            ]
          },
          {
            "id": 21,
            "type": "MultipleChoiceQuestion",
            "content": "Do you know if you are currently affiliated with any Group Purchasing Organization?",
            "position": 3,
            "required": true,
            "has_questions": true,
            "next_question_id": 23,
            "prev_question_id": 20,
            "questions": [{
              "id": 22,
              "type": "MultipleSelectQuestion",
              "content": "With which GPO are you affiliated?",
              "position": 1,
              "required": true,
              "has_questions": false,
              "next_question_id": null,
              "prev_question_id": null
            }],
            "question_options": [{
                "id": 81,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 82,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              },
              {
                "id": 83,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 3
              }
            ]
          },
          {
            "id": 23,
            "type": "MultipleChoiceQuestion",
            "content": "Would you be interested in purchasing high-quality, brand-name products you are familiar with at prices that are the same or better than your current distributor's private label brand?",
            "position": 4,
            "required": true,
            "has_questions": false,
            "next_question_id": 24,
            "prev_question_id": 21,
            "question_options": [{
                "id": 90,
                "input": "radio",
                "data_type": "boolean",
                "label": "Yes",
                "name": "yes",
                "position": 1
              },
              {
                "id": 91,
                "input": "radio",
                "data_type": "boolean",
                "label": "No",
                "name": "no",
                "position": 2
              },
              {
                "id": 92,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 3
              }
            ]
          },
          {
            "id": 24,
            "type": "MultipleSelectQuestion",
            "content": "Rank the following concerns that you have with your current distribution (scale of 1-10 with 1 meaning not a concern at all and 10 being a major concern).",
            "position": 5,
            "required": true,
            "has_questions": false,
            "next_question_id": 25,
            "prev_question_id": 23,
            "question_options": [{
                "id": 93,
                "input": "range",
                "data_type": "integer",
                "label": "Pricing",
                "name": "pricing",
                "position": 1
              },
              {
                "id": 94,
                "input": "range",
                "data_type": "integer",
                "label": "Product Availability/Backorders",
                "name": "availability",
                "position": 2
              },
              {
                "id": 95,
                "input": "range",
                "data_type": "integer",
                "label": "Product Quality",
                "name": "quality",
                "position": 3
              },
              {
                "id": 96,
                "input": "range",
                "data_type": "integer",
                "label": "Customer Service",
                "name": "service",
                "position": 4
              },
              {
                "id": 97,
                "input": "range",
                "data_type": "integer",
                "label": "Accessibility/Availability of your account manager",
                "name": "manager",
                "position": 5
              },
              {
                "id": 98,
                "input": "range",
                "data_type": "integer",
                "label": "Equipment repair and availability of loaner equipment",
                "name": "equipment",
                "position": 6
              },
              {
                "id": 99,
                "input": "range",
                "data_type": "integer",
                "label": "Accounting (invoicing, statements, credits and returns)",
                "name": "accounting",
                "position": 7
              },
              {
                "id": 100,
                "input": "range",
                "data_type": "integer",
                "label": "Ease of Ordering",
                "name": "ordering",
                "position": 8
              },
              {
                "id": 101,
                "input": "range",
                "data_type": "integer",
                "label": "Pricing",
                "name": "pricing",
                "position": 9
              }
            ]
          },
          {
            "id": 25,
            "type": "MultipleSelectQuestion",
            "content": "From which distributor are you currently buying medical supplies?",
            "position": 6,
            "required": true,
            "has_questions": false,
            "next_question_id": 26,
            "prev_question_id": 24,
            "question_options": [{
                "id": 102,
                "input": "radio",
                "data_type": "boolean",
                "label": "McKesson",
                "name": "mckesson",
                "position": 1
              },
              {
                "id": 103,
                "input": "radio",
                "data_type": "boolean",
                "label": "Henry Schein",
                "name": "henry_schein",
                "position": 2
              },
              {
                "id": 104,
                "input": "radio",
                "data_type": "boolean",
                "label": "Medline",
                "name": "medline",
                "position": 3
              },
              {
                "id": 105,
                "input": "text",
                "data_type": "string",
                "label": "Other",
                "name": "other",
                "position": 4
              },
              {
                "id": 106,
                "input": "radio",
                "data_type": "boolean",
                "label": "No Answer",
                "name": "no_answer",
                "position": 5
              }
            ]
          },
          {
            "id": 26,
            "type": "FreeTextQuestion",
            "content": "Is there anything else that I haven't covered that you feel is important when evaluating or selecting a supplier?",
            "position": 7,
            "required": false,
            "has_questions": false,
            "next_question_id": 27,
            "prev_question_id": 25,
            "question_options": [{
              "id": 107,
              "input": "textarea",
              "data_type": "string",
              "label": null,
              "name": "evaluating_supplier",
              "position": 1
            }]
          },
          {
            "id": 27,
            "type": "FreeTextQuestion",
            "content": "If you could change one thing about your current supplier what would it be and why?",
            "position": 8,
            "required": false,
            "has_questions": false,
            "next_question_id": null,
            "prev_question_id": 26,
            "question_options": [{
              "id": 108,
              "input": "textarea",
              "data_type": "string",
              "label": null,
              "name": "change_supplier",
              "position": 1
            }]
          }
        ]
      }
    }
  }
```

## Create QuestionAnswer

This endpoint creates a single question answer.

### HTTP Request

<code>POST http://democrasales.com/api/v1/question_answers</code>

Parameter | Required | Description
----------| ------- | -----------
question_id | required | question ID
question_option_id | required | question option id
value | required | The serialized string value of answer. The data type is determined by the associated QuestionOption.

> The response looks like this:

```shell
{
  "id": 15,
  "question_id": 1,
  "question_option_id": 4,
  "value": 'true'
}
```

## Bulk Create QuestionAnswer

This endpoint creates multiple question answers.

### HTTP Request

<code>POST http://democrasales.com/api/v1/question_answers/bulk_create</code>

Parameter | Required | Description
----------| ------- | -----------
question_answers | required | array of question answers, each containing <b>question_id</b>, <b>question_option_id</b>, and <b>value</b>

> The response looks like this:

```shell
[{
  "id": 15,
  "question_id": 1,
  "question_option_id": 4,
  "value": '6'
},
{
  "id": 16,
  "question_id": 1,
  "question_option_id": 6,
  "value": '2'
}]
```

## Update QuestionAnswer

This endpoint updates a single question answer.

### HTTP Request

<code>PUT http://democrasales.com/api/v1/question_answers/:id</code>

Parameter | Required | Description
----------| ------- | -----------
id | required | question answer ID
value | required | The serialized string value of answer. The data type is determined by the associated QuestionOption.

> The response looks like this:

```shell
{
  "id": 15,
  "question_id": 1,
  "question_option_id": 4,
  "value": 'true'
}
```

## Bulk Update QuestionAnswer

This endpoint updates multiple question answers.

### HTTP Request

<code>PUT http://democrasales.com/api/v1/question_answers/bulk_update</code>

Parameter | Required | Description
----------| ------- | -----------
question_answers | required | array of question answers, each containing <b>id</b> and <b>value</b>

> The response looks like this:

```shell
[{
  "id": 15,
  "question_id": 1,
  "question_option_id": 4,
  "value": '6'
},
{
  "id": 16,
  "question_id": 1,
  "question_option_id": 6,
  "value": '2'
}]
```
