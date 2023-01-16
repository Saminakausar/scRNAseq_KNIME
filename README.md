# scRNAseq_KNIME workflow: A Customizable, Locally Executable, Interactive and Automated KNIME workflow for scRNA seq.

## Instructions for using the scRNAseq\_KNIME workflow

### Outline

1. **Download R and Rstudio** 
1. **Download R packages required for scRNA-seq analysis**  
1. **Introduction to KNIME platform** 
1. **Downloading, installing and configuring scRNAseq\_KNIME workflow for scRNA-seq analysis**  
1. **KNIME documentation** 
1. **Step by step tutorial of scRNAseq\_KNIME workflow using the test dataset** 
1. **Frequently Asked Questions (FAQ)** 


 ### 1. Download R and Rstudio

Download and install R from the following link: [https://cran.r-project.org/ ](https://cran.r-project.org/) 

Download and install Rstudio from the following link: [https://www.rstudio.com/products/rstudio/ ](https://www.rstudio.com/products/rstudio/) 

Instructions for installing R and Rstudio can be found here:[ https://rstudio- education.github.io/hopr/starting.html ](https://rstudio-education.github.io/hopr/starting.html)[https://techvidvan.com/tutorials/install-r/ ](https://techvidvan.com/tutorials/install-r/) 

- Please note that R-4.2.0 version was used for workflow development 

### 2. Download R packages required for scRNA-seq analysis

**Following R packages are required to run the workflow** 

- Rserve** 
- Seurat 
- dplyr 
- patchwork 
- ggplot2 
- plotly 

**To install an R package, run the following R functions in the R environment or in Rstudio:** 

install.packages("Rserve", dependencies = TRUE)** install.packages("dplyr", dependencies = TRUE)** install.packages("ggplot2", dependencies = TRUE)** install.packages("Seurat", dependencies = TRUE)** 

**NOTE: To install seurat package you may need to install Devlib or developer** 

**libraries. Also,sometimes, seurat installation using R/Rstudio has issues in linux.**  

**In this case you can install seurat using the a command in the terminal.  Just run the following commands one by one:** 

- sudo apt-get install build-essential  
- sudo su - \ -c "R -e \"install.packages('Seurat', repos=['https://cran.rstudio.com/'](https://cran.rstudio.com/))\"" 

Installing plotly for R: 

install.packages('remotes') remotes::install\_github('plotly/plotly.R') 

**To check if all the packages are correctly installed, run the following R code in R/Rstudio** 

library(Rserve) library(Seurat) library(dplyr) library(patchwork) library(ggplot2) library(plotly) 

**NOTE:  For MacOS, following packages would also be required to run the workflow. Run the following function in R/Rstudio** 

- install.packages("Cairo", dependencies = TRUE) 
- Check if the Cairo package is installed. Run the following R code in R/Rstudio 

library(Cairo**)**

- On Mac OS X if you use RStudio or R, you must have a copy of XQuartz, the X11 window manager, installed. This is no longer a default install since Mac OS X 10.8. You need to install XQuartz 

●  Please download and install XQuartz from[ http://www.xquartz.org/ ](http://www.xquartz.org/) 

3. **Introduction to KNIME platform, the Konstanz Information Miner** 

KNIME  (https://www.knime.com/)  is  an  open  source  platform  for  data  analysis, manipulation, and reporting. KNIME aims to advance the impact and understanding of data science through visual programming using predefined components called nodes. **Nodes** are basic processing units of KNIME workflows that perform particular tasks on data. KNIME Workflows combine different nodes to model the data analysis flow. Below are  the  resources  to  know  more  about  KNIME  interface,  components  and  their executions.  

- **KNIME workbench:**  

[https://docs.knime.com/2018- 12/analytics_platform_workbench_guide/index.html#the-knime-workbench** ](https://docs.knime.com/2018-12/analytics_platform_workbench_guide/index.html#the-knime-workbench)

![](Aspose.Words.c2834ef4-e5e7-45d3-b421-1b036cd0c900.001.png)

Figure 1:** KNIME interface with its different sections 

- **KNIME Workspaces:** 

[**https://docs.knime.com/2018- 12/analytics_platform_workbench_guide/index.html#workspaces ](https://docs.knime.com/2018-12/analytics_platform_workbench_guide/index.html#workspaces)** 

- **KNIME Nodes** 

[**https://docs.knime.com/2018- 12/analytics_platform_workbench_guide/index.html#workflow-editor-nodes ](https://docs.knime.com/2018-12/analytics_platform_workbench_guide/index.html#workflow-editor-nodes) **Video link (What is a Node? What is a Workflow?):   [https://www.youtube.com/watch?v=4rETNe- Xx7k&list=RDCMUCRbKmV_XYB7C12SPBokLVHQ&index=8** ](https://www.youtube.com/watch?v=4rETNe-Xx7k&list=RDCMUCRbKmV_XYB7C12SPBokLVHQ&index=8)**

- **How to Create, Configure, Reset, Execute a Node/group of nodes/full workflow and visualize each node output** 

Video link:[** https://www.youtube.com/watch?v=fMM_w4v5zZc ](https://www.youtube.com/watch?v=fMM_w4v5zZc) 

4. **Downloading, installing and configuring scRNAseq\_KNIME workflow for scRNA-seq analysis** 
- **Download KNIME from the following links: [https://www.knime.com/download-installer/2/64bit ](https://www.knime.com/download-installer/2/64bit)**(For windows) [https://www.knime.com/download-installer/6/64bit ](https://www.knime.com/download-installer/6/64bit)(For Linux) [https://www.knime.com/download-installer/8/64bit ](https://www.knime.com/download-installer/8/64bit)(For macOS)
- **Once downloaded, proceed with installing KNIME Analytics Platform:** 
  - Windows: Run the downloaded installer or self-extracting archive.  
  - Linux: Extract the downloaded tarball to a location of your choice. Run the KNIME executable to start KNIME Analytics Platform. 
  - Mac: Double click the downloaded dmg file and wait for the verification to finish. Then move the KNIME icon to Applications. Double click the KNIME icon in the list of applications to launch KNIME Analytics Platform. 

**Video link** (**installing, launching and defining the working environment**): [https://www.youtube.com/watch?v=8ISIeFKkoOE ](https://www.youtube.com/watch?v=8ISIeFKkoOE) 

- **Increase KNIME memory to handle big data and to increase the** 

**processing speed**  

1. Go to KNIME directory (where KNIME is installed) 
1. Open **knime.ini** (configuration settings) file 
1. Increase memory given in MB ( Xmx...m) \*here m is for MB just change number between **Xmx** and **m** (you can increase memory according to your requirements and given computer specifications/capacity) 
1. **Setting up knime.ini:[ https://docs.knime.com/2018- 12/analytics_platform_workbench_guide/index.html#setting-up- knime-ini ](https://docs.knime.com/2018-12/analytics_platform_workbench_guide/index.html#setting-up-knime-ini)** 
- **Install KNIME extensions** 

`                 `Before running the workflow we need to install KNIME extensions. You can                      install all the available extensions in the list. It's a simple step follow the      

`                 `following instructions: 

1. open file -> install KNIME extensions -> Select all extensions-> click Next 
- **Set path to R:**    
2. Run following function in R/Rstudio to find the path to R home 

`            `R.home()  

3. Open file -> preferences -> KNIME -> R (Browse R directory (path to the folder where R is Installed)). For example in R/RStudio on Linux, R.home() function returns path to R is "/usr/lib/R"

**NOTE: Make sure path is set to R home where all packages were installed** 

- **Import workflow** 

Open file -> Import KNIME Workflow -> select file (Browse the **scRNAseq\_KNIME\_workflow.knwf** file) .knwf is file extension to specify KNIME workflow 

**Video link (How to import and export KNIME Workflows):   [ https://www.youtube.com/watch?v=4GiwmM-qcC4 ](https://www.youtube.com/watch?v=4GiwmM-qcC4)** 

**5. KNIME documentation** 

- **KNIME Analytics Platform Installation Guide:  [https://docs.knime.com/latest/analytics_platform_installation_guide/index. html#_installing_knime_analytics_platform ](https://docs.knime.com/latest/analytics_platform_installation_guide/index.html#_installing_knime_analytics_platform)**
- **KNIME Workbench Guide:** 

[https://docs.knime.com/2018- 12/analytics_platform_workbench_guide/index.html#workspaces ](https://docs.knime.com/2018-12/analytics_platform_workbench_guide/index.html#workspaces)
7 
