## Table of contents

- [Introduction](#introduction)
- [Inputs](#inputs)
- [Usage](#usage)

## Introduction

This action lets you retrieve page details from the Notion API, exposing them as action outputs that can be used in subsequent steps.

## Inputs

| input            | description                  | required |
| ---------------- | ---------------------------- | -------- |
| `notion_api_key` | Notion API Key               | `true`   |
| `page_id`        | Identifier for a Notion page | `true`   |

## Usage

```yml
name: Print page URL
on:
  pull_request:
    types: [opened]
jobs:
  notion:
    runs-on: ubuntu-latest
    steps:
      - name: Retrieve page details
        id: page_details
        uses: dovetail/notion-get-page@latest
        with:
          notion_api_key: secret_1234567890abcdef1234
          page_id: 1234567890abcdef1234567890abcdef
      - run: |
          echo ${{ steps.page_details.outputs.url }}
```
