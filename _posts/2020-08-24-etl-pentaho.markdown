---
layout: post
title:  "ETL Project - Pentaho Data Integration"
date:   2020-08-24
description: This is a post description for a ETL process using the software Pentaho Data Integration.
---

<p class="intro"><span class="dropcap">E</span>xtract, transform, load (ETL), commonly used to build a Data Warehouse. In this process, data is taken (extracted) from one or more source systems or sources, converted (transformed) into a format that can be analyzed, and stored (loaded) in a warehouse or another system, as you can see in Fig1.</p>

<figure>
	<img src="{{ '/assets/img/bi_process.png' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig1. - BI Project Process</figcaption>
</figure>

This project describes the complete ETL process in Pentaho Data Integration. From excel tables and csv files as the data source, it will be modeled a **Data Warehouse (DW)**.

The data source follows a relational model as shown in Fig2.

<figure>
	<img src="{{ '/assets/img/staging.jpg' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig2. - Relational Model of the Data Sources</figcaption>
</figure>

From this data source, the objective is to model a DW as a star scheme in Fig 3, which is the most recommended scheme to optimize performance in a BI project.

The model is composed in the center by a Fact table, surrounded by dimensions, looking like the shape of a star. 

The fact tables are the central tables and have data on numerical measures respresenting information about business performance and dimensional tables must contain all the descriptions that are necessary to define a class as Product, Time or Client.

<figure>
	<img src="{{ '/assets/img/dw_model.jpg' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig3. - Star Scheme of the Data WareHouse</figcaption>
</figure>

MySQL via Workbench was used as repository for the data source and MySQL via XAMPP for the DW. This was done using the following sql commands:

#### For Workbench
{% highlight sql %}
CREATE SCHEMA IF NOT EXISTS STAGE DEFAULT CHARACTER SET utf8;
{% endhighlight %}

#### For XAMPP
{% highlight sql %}
CREATE SCHEMA IF NOT EXISTS DW DEFAULT CHARACTER SET utf8;
{% endhighlight %}

First step is **Extraction**, bringing the data from the sources to the staging area, which is a temporary area, necessary due to the heterogeneity existing in the information coming from these systems.

<figure>
	<img src="{{ '/assets/img/Origem.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig4. - Staging Area</figcaption>
</figure>

After Extraction, the necessary inputs were collected to start the **Transformation** and cleaning step. In this phase, deviations and inconsistencies are corrected, standardized and treated, transforming the data according to the business rules. 

Finally, the last step is **Load** to the DW, which was done according to the star scheme (Fig3) to construct the dimensions and the fact table. 

#### Product Dimension
<figure>
	<img src="{{ '/assets/img/Dim_Product.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig5. - Product Dimension</figcaption>
</figure>


#### Client Dimension
<figure>
	<img src="{{ '/assets/img/Clients Dimension.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig6. - Client Dimension</figcaption>
</figure>


#### Employees Dimension
<figure>
	<img src="{{ '/assets/img/Dim_Employees.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig7. - Employees Dimension</figcaption>
</figure>


#### Time Dimension
<figure>
	<img src="{{ '/assets/img/Dim_Data.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig8. - Time Dimension</figcaption>
</figure>


#### Fact Table
<figure>
	<img src="{{ '/assets/img/Fact_table.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig9. - Fact Table</figcaption>
</figure>




