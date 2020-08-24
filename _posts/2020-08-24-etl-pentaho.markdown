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

This project describes the complete ETL process in Pentaho Data Integration. From excel tables and csv files as the data source, we will model a DW.

The data source follows a relational model as shown in Fig2.

<figure>
	<img src="{{ '/assets/img/staging.jpg' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig2. - Relational Model of the Data Sources</figcaption>
</figure>

From this data source, the objective is to model a Data Warehouse (DW) as a star scheme in Fig 3, which is the most recommended scheme to optimize performance in a BI project.

<figure>
	<img src="{{ '/assets/img/dw_model.jpg' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig3. - Star Scheme of the Data WareHouse</figcaption>
</figure>

MySQL via Workbench was used as repository for the data source and MySQL via XAMPP for the DW. This was using the following sql commands:

## For Workbench
{% highlight sql %}
CREATE SCHEMA IF NOT EXISTS STAGE DEFAULT CHARACTER SET utf8;
{% endhighlight %}

## For XAMPP
{% highlight sql %}
CREATE SCHEMA IF NOT EXISTS DW DEFAULT CHARACTER SET utf8;
{% endhighlight %}

First step is the extraction, bringing the data from the sources to the staging area, which is a temporary area, necessary due to the heterogeneity existing in the information coming from these systems.

<figure>
	<img src="{{ '/assets/img/Origem.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig3. - Staging Area</figcaption>
</figure>




