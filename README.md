# Assignment 3: Interactive Dashboard
## Data on Harassment or Bullying Estimations by Basis Category (2013-14, Office for Civil Rights)

## Visualization Technique (25%)

### 1. A narrative description of each visualization type in your dashboard
   
   My dashboard comprises four distinct visualization types, each designed to explore and present the harassment and bullying data from the 'Data on Harassment or Bullying dataset' in unique ways, with a particular emphasis on Black or African American students alongside broader categories.

   - **1.1. Plotly Express US Map (Choropleth) Black or African American Students:** This choropleth map visually represents the percentage of Black or African American students who have experienced bullying or harassment across different states in the United States. The shading follows a continuous gradient, where darker shades indicate higher percentages. This visualization allows for quick and immediate geographical comparison and highlights regional patterns in bullying rates.
   - **1.2. Bar Graph – Black or African American Students by State:** The bar graph presented the same data as the choropleth map but in a state-by-state comparison using bars instead of a gradient colors and state borders. This visualization is beneficial for quickly identifying which states have the highest, lowest, and similar reported bullying/harassment rates, making direct numerical comparisons easier.
   - **1.3. Bar Graph – Black or African American Students by State and Sex:** This visualization expanded on the previous bar chart by introducing gender as an additional categorical variable. The bars are color-coded (e.g., blue for male students, red for female students) to easily distinguish between the two groups. This approach makes it easier to see gender-based differences within each state, helping to determine if one gender reports significantly higher rates of bullying than the other.
   - **1.4. Interactive Choropleth Map – Multiple Categories of Bullying/Harassment** This interactive map allowed me to explore bullying and harassment across multiple demographic categories (i.e., different racial/ethnic groups, students with disabilities, English Language Learners (ELL)). The dropdown menu enables dynamic selection of categories, updating the map accordingly. This visualization offers a flexible, exploratory approach to understanding bullying trends among various student groups.

   
### 2. A discussion of how these visualizations complement each other and when each should be used
- **The static choropleth map (Chart 1.1)** provided an immediate geographic snapshot of Black or African American student harassment/bullying, making it easy to spot regional trends (e.g., higher rates in the Southeastern US).
- **The state-by-state bar graph (Chart 1.2)** zoomed into this same data, offering higher precision and direct comparison across all 52 regions regardless of state size, which 1.1's map and color gradient might have obscured, especially for close values.
- **The sex-split bar graph (Chart 1.3)** built on this by adding a new dimension, sex, allowing for immediate comparison between the two sexes on a state-by-state basis.
- Ultimately, the **interactive choropleth map (Chart 1.4)** broadened the scope beyond Black or African American students to all categories, allowing users to explore how harassment and bullying varied across the different groups of the study (e.g., comparing Black students to White, IDEA, or ELL students) with the same geographic lens as Chart 1.1. Together, the four charts transitioned from a focused racial analysis to a more comprehensive, category-wide perspective cross-country.

    When to use each:
    - **Chart 1.1 (Static Choropleth):** I can use this when I want a quick, high-level overview of Black or African American (or other basis) student harassment across the U.S. This chart is ideal for introductions to the data, presentations, or initial data exploration to identify regional "hotspots".
    - **Chart 1.2 (Bar Graph by State):** I can use this graph for when I want a detailed, quantitative comparison of Black student harassment across all states (and not get hindered by color values or state shapes/borders), especially when I want to pinpoint exact percentages (e.g., "Is California's percentage for ___ higher than Texas'?") or even ranking states across a specific basis.
    - **Chart 1.3 (Bar Graph by State and Gender):** I can use this for when I want to analyze gender differences within a specific basis of harassment/bullying in a certain state. This may prove especially helpful in high-incidence states in an effort to better understand if certain policies should target male or female students differently.
    - **Chart 1.4 (Interactive Choropleth):** I can use this for when I want to prioritize flexibility and user-driven exploration across all student categories. This is especially true for when we want to do in-depth analyses or when we want interactive settings (e.g., a classroom or meeting demo) where stakeholders might want to to compare multiple groups like race, disability, or language status.

### 3. Dashboard-specific considerations like interactivity options
- ** Chart 1.1:** This static map has basic interactivity, such as hover tooltips (state, total students, percentage). It is adequate for quick glances without overwhelming the user. The express map is quick to generate and additional interactivity wasn’t added to keep it simple and focused.
- ** Chart 1.2:** Similar to 1.1, this bar chart includes hover tooltips and percentage labels above bars, with no additional interactivity to maintain clarity across 52 bars—dropdowns or filters, as these would have cluttered the already dense display.
- ** Chart 1.3:** The gender bar chart also utilizes hover and text labels, with color differentiation (blue for male students, red for female students) as a visual cue instead of interactivity.
- ** Chart 1.4:** The standout interactive feature here is the dropdown menu, allowing users to switch between all basis categories. The hover info updates dynamically (e.g., "Black or African American: [value]%"), and the title and color range adjust to the selected data, enhancing usability and application of the data. I initially explored JupyterDash for more interactivity (e.g., clickable states and generative bar graphs for each state), but server errors led me to Plotly’s native dropdowns, which proved simpler and effective for my purposes


## Visualization Library (25%)
#### 1. The dashboard framework and libraries you're using, and why they're suitable for this visualization. For instance, who created it? Is it open source? How do you install it?
- Before this course, I hadn't used any interactive graphic libraries for Python. However, with some Googling, I quickly found out about Plotly (`plotly.py`). As it turns out, Plotly is a widely-used, **interactive, open-source, and browser-based** graphing library for Python -- making it an ideal choice for this project.
- Plotly was developed by Plotly Inc., and was founded in 2013 by Alex Johnson, Jack Parmer, Chris Parmer, and Matthew Sundquist. Because Plotly is open-source under the MIT license, it is freely available and community-supported.  Its website [https://dash.plotly.com/dash-in-jupyter] offers Jupyter-friendly API, as well as loads of examples, pictures, and explanations for its applications. Ultimately, I chose Plotly for its interactivity, well-documented website, Jupyter compatibility, and open-source accessibility.
- Installation is straightforward: we can use use pip (`pip install plotly`) for the core Plotly library, or we can use conda (`conda install -c conda-forge plotly`).


#### 2. A discussion of the general approach and limitations of this framework. For instance, Is it declarative or procedural? Does it integrate with Jupyter? Why did you decide to use this framework (especially if there are other options)?
- In a declarative framework, you specify *what* you want to visualize (e.g., a choropleth map with state codes and percentage data) rather than *how* to draw it step-by-step. In this sense, I believe my general approach with Plotly is a mix of declarative and procedural.
- When I first used Plotly to create my initial choropleth map with **Plotly Express** (i.e., with `px.choropleth(df_total, locations="State Code", color="American Indian or Alaska Native (Percent)")`), all I had to do was define the data and desired output, and Plotly handled the rendering. Plotly Express's simplicity sped up the coding process and, as a beginner, I appreciated how it offered me an introduction where I didn’t need to manage lower level graphics details.
- However, I quickly found that, to add interactivity like dropdowns and a bar chart subplot, I had to switch to to **Plotly Graph Objects** (`go`), which was more procedural. This required me to explicitly define traces (e.g., `go.Bar`) and layouts, which offered me greater control, but also increased my code's complexity and need to debug.
- Plotly integrates exceptionally well with Jupyter Notebooks, which was one of the key reasons I chose it for this assignment. An almost-equally important reason for choosing it was its innate USA Map feature, which I knew would be a key component for my data. Furthermore, with Plotly, when I typed `fig.show()`, the respective charts would render directly in the Jupyter notebook cells; and interactive features like hover tooltips and dropdowns worked without me having to leave the environment.
- I decided to use Plotly over other options like `Matplotlib`, `Seaborn`, or `Vega-Altair` (all of which I was more familiar with due to past courses) because they lacked *native interactivity* - a key component in this project.


## Demonstration (50%)

1. The dataset you picked and instructions for cleaning the dataset. You should pick a suitable dataset to demonstrate multiple visualization types and interactive features working together.
2. The quality of your demonstration. First demonstrate building basic dashboard components, then show how to implement interactivity and advanced features. This is the "meat" of the assignment. For reference you should have at least 4 graph types in your dashboard that work together to tell a cohesive story.

## Deliverables
- Code Repository (git repo or zip file)
  - Complete dashboard source code Development setup instructions
  - All necessary dependencies and assets/datafiles
- Tutorial Document (pdf)
  - Written tutorial covering all visualization implementations. Include screenshots and code snippets
  - Troubleshooting of any common errors you encountered
- Final Dashboard
  - Deployed version of your dashboard, with interactivity
  - Example dataset included


## Import Libraries
I installed the following libraries to clean the data and to create the visualizations needed for this assignment:

```
import pandas as pd
import plotly.express as px        # For initial testing purposes with Plotly and Chart 1.1
import plotly.graph_objects as go  # For more complex Plotly charts (Charts 1.2-1.4)
```

