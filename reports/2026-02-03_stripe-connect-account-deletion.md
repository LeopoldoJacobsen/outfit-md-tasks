# Stripe Connect Account Deletion Report

**Date:** February 3, 2026  
**Reported By:** Leopoldo Jacobsen  
**Status:** ✅ Resolved

---

## Summary

| Field | Details |
|-------|---------|
| **Time Started** | 1:40 PM EST |
| **Time Resolved** | 1:43 PM EST |
| **Resolution Time** | ~3 minutes |
| **Account ID Deleted** | `acct_1SwnNgHFm8JbrFvk` |

## Issue

A Stripe Connect account was created with an incorrect business/legal name. Stripe does not permit editing the name of a Connect account after creation, requiring deletion and recreation.

## Root Cause

Human error during initial account creation — incorrect name was entered.

## Resolution

1. Located the Connect account ID from the Stripe Dashboard
2. Used the [Stripe API Delete Account endpoint](https://docs.stripe.com/api/accounts/delete) to remove the account
3. Executed via `curl` command with proper authentication
4. Confirmed deletion with API response: `"deleted": true`

## Technical Details

**API Endpoint Used:**
```
DELETE https://api.stripe.com/v1/accounts/{account_id}
```

**Response:**
```json
{
  "id": "acct_1SwnNgHFm8JbrFvk",
  "object": "account",
  "deleted": true
}
```

## Follow-Up Actions

- [ ] Create new Connect account with correct name
- [ ] Regenerate Stripe API key (security best practice)
- [ ] Update any integrations referencing the old account ID

## Lessons Learned

- Double-check business/legal name before creating Connect accounts
- Connect account names cannot be changed after creation
- Deletion via API is fast and straightforward when needed
