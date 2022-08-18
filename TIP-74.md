---
id: tip-74
title: TIP-74: Market Description Input Field for Ex0t1cs
status: Draft
author: Millie
discussions-to: https://discord.gg/nDtrdx9B
hide_title: false
sidebar_label: TIP-74
---

## Simple Summary
 
This TIP proposes to introduce an optional input for Exotic markets creation. This input would be in the form of a string similar to the market question and will serve as an optional market summary that describes the market in detail and provides context for users
 
## Motivation

After some community feedback since the launch of Exotic markets, one of the main suggestions from the community was to provide more information about each market and better outline the intentions of the market creator so as to remove random ambiguities.

Upon consideration the Oracle Council decided that a market summary box is as an optional input field for market creation is a sound idea and likely improvement of the current user experience. 


## Specification

At time of market creation, give creators an optional string input field capped at 1000 charachters which is to represent a summary of the market that is being created. 
The Purpose of this optional input is not to restate the market question, but to provide context about the market. The Market discription must not contain another question in it and must not give a description of the market which contradicts the market question or any of the other input fields (eg: use of conflicting dates or event details/participants than what is used in other input fields) 
This TIP is to be accompanied with a Guideline change which represents the conditions above.

The Market Description field is to contain background information about the market and the event that it's tracking. URLs and event coverage links are permitted for use in this input field.
Although the text in the market description is not directly subject to dispute for impercise language or grammatical errors, it can be subject to dispute for containing contradictory information with other input fields and any irrelevant (spam) content.

This input field is optional so not including it upon market creation is acceptable, and the use of it is only disputable if the content contradicts the rest of the market details, poses another question or contains spam.

## Test Cases
TBD

## Implementation
TBD

## Copyright
 
Copyright and related rights waived via CC0.
