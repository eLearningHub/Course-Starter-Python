name: Node

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2.3.1
        
      - name: npm install and build
        run: |
          npm install
          npm run build
 
      - name: Deploy	
        uses: peaceiris/actions-gh-pages@v3	
        with:	
          github_token: ${{ secrets.GITHUB_TOKEN }}	
          publish_dir: ./public
