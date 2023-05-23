# lab04
```
mkdir TP-LAB04
cd TP-LAB04
mkdir .github
cd .github
mkdir workflows
cd workflows
touch CI.yml
nano CI.yml
```

```
name: CMake

on: 
 push:
  branches: [main]
 pull_request:
  branches: [main]

jobs: 
 build_Linux: 

  runs-on: ubuntu-latest 

  steps: 
  - uses: actions/checkout@v3

  - name: Configure Solver 
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build

  - name: Build Solver 
    run: cmake --build ${{github.workspace}}/solver_application/build

  - name: Configure HelloWorld 
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build

  - name: Build HelloWorld 
    run: cmake --build ${{github.workspace}}/hello_world_application/build
 ```
Заливаю на гит:

``` 
git add -A
git commit -m "commit"   
git push origin main
```

Все тесты пройдены!
