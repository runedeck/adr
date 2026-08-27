---
title: "${TITLE}"                          %% short noun phrase %%
description: "${DESCRIPTION}"              %% the decision in one sentence %%
type: adr
category: "${CATEGORY}"                    %% architecture | process | security %%
tags: []
status: ${STATUS}                          %% proposed | accepted | deprecated | superseded %%
created: ${DATE}                           %% YYYY-MM-DD %%
updated: ${DATE}
author: "${AUTHOR}"                        %% @handle %%
project: "${PROJECT}"
related: []                                %% neighbor records, by name %%
upstream: []                               %% sources this decision follows %%
responsible: ["${AUTHOR}"]                 %% RACI: who does the work %%
accountable: ["${OWNER}"]                  %% RACI: who approves %%
consulted: []
informed: []
---

# ${TITLE}

## Context and Problem Statement

${CONTEXT}                                 %% the forces and the question, one paragraph %%

## Considered Options

1. ${OPTION_ONE}
2. ${OPTION_TWO}

## Decision Outcome

Chosen option: ${CHOICE}.

${RULE}                                    %% the rule the decision sets, stated plainly %%

### Consequences

- [+] ${POSITIVE}                          %% what improves %%
- [-] ${NEGATIVE}                          %% the accepted cost %%
