# Set Masked Env

Set masked environment variables in workflow.  
The log when using the set environment variable will remain `masked` If you read the information registered in GitHub Secrets and set it in the environment variable.

## Examples
```yml
name: example
on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: Restore Env File
        run: echo ${{ secrets.FILE }} > ./.env
      
      - name: set masked environment variables
        uses: koheing/set-masked-env@v1.0
        with:
          filePath: ./.env
          # mask: false // option

      - name: Print
        run: echo "$HELLO"
        # Output: ***
```

## Inputs

### **filePath** (**required**)
Specify the path of the file you'd like to read as an environment variable.

### mask (option)
Default `true`. Set to false if you wouldn't want to mask.
