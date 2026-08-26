# Interview Assignment

## 1. Semantic Chunk Retrieval

### Problem Statement

Given a user query and 10 text chunks, generate embeddings and return the top 3 semantically most relevant chunks.

### User Query

> What documents are required to open a current account for a private limited company?

### Sample Data

```python
chunks = [
    {
        "id": "C1",
        "text": "To open a current account for a private limited company, submit Certificate of Incorporation, PAN, Memorandum and Articles of Association, board resolution and KYC of authorised signatories.",
    },
    {
        "id": "C2",
        "text": "Savings account customers must provide PAN, Aadhaar, photograph and residential address proof.",
    },
    {
        "id": "C3",
        "text": "Current accounts are suitable for businesses with frequent transactions and usually do not earn interest.",
    },
    {
        "id": "C4",
        "text": "Partnership firms must submit partnership deed, firm PAN and KYC documents of partners.",
    },
    {
        "id": "C5",
        "text": "Corporate current account applicants must provide company registration documents, tax identification details and authorised signatory information.",
    },
    {
        "id": "C6",
        "text": "Home loan applicants must submit income proof, bank statements, employment details and property documents.",
    },
    {
        "id": "C7",
        "text": "Dormant accounts can be reactivated after identity verification and submission of a reactivation request.",
    },
    {
        "id": "C8",
        "text": "For company accounts, banks must verify legal existence, beneficial ownership, authorised signatories and board authority to operate the account.",
    },
    {
        "id": "C9",
        "text": "Business debit cards may have daily ATM and point-of-sale transaction limits.",
    },
    {
        "id": "C10",
        "text": "GST registration certificates may be accepted as supporting proof of business activity.",
    },
]
```

### Suggested Models

- `gemini-embedding-001`
- `sentence-transformers/all-MiniLM-L6-v2`
- `BAAI/bge-small-en-v1.5`

## 2. RAG Output Evaluation

### Problem Statement

Given a user query, retrieved context and generated answer, evaluate the quality of the RAG output and determine whether the issue is mainly retrieval, generation, both, or neither.

### Case 1

#### Query

> Can a customer close a fixed deposit before maturity, and what penalty applies?

#### Retrieved Context

- `C1`: Customers may request premature closure of a fixed deposit.
- `C2`: Premature withdrawal attracts a penalty of 1% on the applicable interest rate.
- `C3`: Fixed deposit tenure may range from 7 days to 10 years.
- `C4`: Senior citizens may receive an additional interest rate on fixed deposits.

#### Generated Answer

> Yes. A fixed deposit can be closed before maturity.
> The bank charges a 2% penalty and the deposit must have completed at least six months.

### Case 2

#### Query

> What documents are required to change the registered address of a company account?

#### Retrieved Context

- `C1`: Savings account holders may update address using Aadhaar or another valid address proof.
- `C2`: Customers may update their mobile number through internet banking.
- `C3`: Company current accounts may have multiple authorised signatories.
- `C4`: Debit card replacement can be requested through mobile banking.

#### Generated Answer

> The company should submit new address proof and a board resolution approving the address change.

### Case 3

#### Query

> What is the maximum daily ATM withdrawal limit for the Platinum Business Debit Card?

#### Retrieved Context

- `C1`: The Platinum Business Debit Card has a maximum ATM cash withdrawal limit of ₹1,00,000 per day.
- `C2`: The card supports domestic and international transactions.
- `C3`: ATM transactions require PIN authentication.

#### Generated Answer

> The maximum daily ATM withdrawal limit is ₹1,00,000.

### Suggested Models

- No model required.
- Optional LLM-as-judge: Gemini Flash model.
