# report-04

**1.Клонируем репозиторий с прошлой лабы**  
```$ git clone https://github.com/Fedorusita/lab-03 lab-4```  

**2.Создаём локально**
```$ mkdir .github```  
```$ cd ~/lab-04/.github```  
```$ mkdir workflows```  
```$ cd ~/lab-04/.github/workflows```  

**3.Создаём Linux.yml**  
```$ cat >> Linux.yml << EOF```  
```> EOF```  
```$ nano Linux.yml```  
**Cодержание Linux.yml**  
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
    
    
**4.Пушим на гит**  


******

**Аналогично с windows, меняем содержание .yml**

name: CMake  

on:  
 push:  
  branches: [main]  
 pull_request:  
  branches: [main]  

jobs:   
 build_Windows: 

  runs-on: windows-latest  

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
