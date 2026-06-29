# Project 1: Up-scaling of runoff station data to the European scale
Authors: Giovanna Limon, Lisa Baron, Eva Herrmann

## Task 1: Describe the data and prediction problem

### Question 1.a: What is the dataset and the prediction problem about scientifically?

The prediction problem is to estimate runoff across Europe. Assessing runoff volume and flow dynamics is essential for understanding ecosystem processes. The main issue is that available data is limited to stations, while continuous spatial coverage is needed for applications such as flood risk assessment and water management. The prediction problem is how to extrapolate station data to the full European cover.

The Gudmundsson and Seneviratne (2015) equation is used as the main reference:

$$Q_{(s,t)} = f(\tau_\lambda(P_{(s,t)}), \tau_\lambda(T_{(s,t)}))$$

Variables are runoff Q (total liquid runoff), precipitation P (kg/m²/s), and temperature T.

Here we aim to calibrate parameters:
- **λ**: the memory window, defining how many past timesteps the model uses to predict today's runoff.
- **f**: the model function, whose parameters depend on the statistical model (Lasso or Random Forest). Hyperparameters are discussed in the next question.

The training dataset includes 15 stations with Q, P, and T. The dataset covers Europe over 30 randomly selected years, giving 360 timesteps (30 years x 12 months). The prediction dataset is the full European gridded dataset. Only P and T are available; Q will be predicted.

### Question 1.b: What's the data source and what does that tell you about the type of the data?

The dataset is a pre-industrial control run of the CESM model. The simulation was initialised using pre-industrial conditions, with 1850 as the reference year. The model was run over a long period of time. The dataset used in this project is a subset covering only Europe, from a randomly selected 30-year time block.

It is important to note that the data source is a model, not observations — no missing values would be found. The data is also stationary; there is no long term trend.
