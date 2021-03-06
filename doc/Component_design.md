# Components List:

## OPMxplore Cheat Sheet

> + opm.load_data()    # load all proteins onto a dataframe
+ opm.sql_search()     # query dataframe: dataframe, sql query string
+ opm.add_query()      # append dataframe_id:dataframe to running dictionary
+ vis.brill_3d()       # 3d plot: choose high level category, pass in a custom dataframe, visualize on 3 axes
+ vis.stat_plot()      # seaborn style swarm and violin plots overlayed on categorical vs numerical axes
+ vis.scatter_plot()   # seaborn style scatter plot
+ interact(plot_wrappers, key to dataframe, args to plot fxns) # to allow drop down widget control of dataframe


1.**Searching for Proteins**: This will let the user search for desired list of membrane protein(s). Usually with a generic name such as "channels".

2.**Displaying features of proteins**: This will let the user get data such as PDBIDs, names of proteins, location of the membrane protein, membrane depth, tilt and transfer energy from water to the membrane.  

3.**Displaying protein visualization**: This will let the user visualize 3D structure of a selected membrane protein from the list.

4.**Displaying channel protein diameter**: This will calculate the diameter of membrane channel proteins.

5.**User interface**: This will let the user search for membrane proteins of interest and view the features of the protein displayed.


# Data

There are two datasets that we use on for this project:

- Protein Databank: This is a database that contains information about the three-dimensional structure of proteins.

- Orientations of Protein Membranes (OPM): OPM website has an detailed list of calculated features of membrane proteins such as tilt, membrane thicknes, transfer energy from water to the membrane.


# Component Design

## 1. Searching for protein:

This component takes the user query and searches PDB for a list of proteins.

**Input**: Customized user query consisting of generic names or feautures that will be used to query PDB.

**Ouptut**: List of proteins that fit the user's customized query from PDB.

**Pseudocode**: Grab user query -> query PDB -> Return list of proteins matching the query from PDB.

The results from this component is the input for the next component- Displaying the features of proteins.


## 2. Displaying features of proteins:

This component matches proteins to the list of proteins in the OPM dataset and results in a dataframe of selected membrane proteins and their features.

**Input**: List of proteins that fit the user's customized query from PDB.

**Output**: Dataframe of membrane proteins and some of their features as calculated in the OPM dataset.

**Pseudocode**: Get list of proteins that fit user query from PDB -> Find matches to proteins in OPM dataset -> Display a the calculated features of the proteins from OPM dataset in a dataframe.

The results of this component displays a list of protein(s) that fit the user query.


## 3. Displaying protein visualizations:

The user can then choose all or some specific proteins from the dataframe displayed in the previous component and can either visualize the results or view their individual 3D structures.

**Input**: Dataframe of interested proteins and their features.

**Output**: Plots of  statistic of the group of proteins or 3D visualization of individual protein.

**Pseudocode**: User selection of protein(s) and Visualization -> Display desired visualization

The results of this component displays the visual information for the user.


## 4.Displaying channel protein diameter:

This component will let the user choose particular channel protein(s) from the dataframe displayed in component 2 and calulate the diameter of the channel.

**Input**: PDB_ID of chosen channel proteins.

**Output**: Diameter will be displayed.

**Pseudocode**: Grab the PDB_ID of selected channel protein(s) -> fetch the PDB files of the selected channel protein(s) -> parse the coordinates -> compute the diameter -> display diameter as a separate column in the dataframe.

The results of this component will display the diameter of a channel protein of interest.


## 5. User Interface:

This component will result in a user interface either jupyter notebook with widgets that allow a user to query and choose proteins and features to display.
