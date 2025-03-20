
<!DOCTYPE html>
<head>
<title>README</title>
<style>
table { border-collapse: collapse;
 width: 100%; }

td, th { border: 1px solid #dddddd;
 text-algn: left;
 padding: 8px; }

code { font-family: Consolas, "courrier new";
 color: #ac3a3a;
 padding: 2px; }

div.Div { border: 1px solid black;
 background-color:#f1f1f1;
 text-align: left;
 width: 500px;
 margin-left: 20px;
 border-radius: 10px;
 padding: 5px; }

hr.hr { border: dotted 2px; }

div.Div2 { background-color:#2c4786;
 text-align: center;
 width: 100%;
 padding: 0px 0px;
 margin: 0;
 color: #FFFFFF;
 top: 0px;
 font-size: 25px; }

div.container { display: flex;
 gap: 25px;
 align-items: flex-start;
 box-sizing: border-box; }

div.box1{ border: 2px solid black;
 background-color:#f1f1f1;
 border-radius: 10px;
 text-align: left;
 max-width: 500px;
 top: 0;
 height: auto;
 padding: 10px; }

div.box2 { border: 2px solid black;
 background-color: #FFFFFF;
 width: 100%;
 margin-right: 10px;
 border-radius: 15px;
 padding: 10px;
 }
body { background-color: #FFFFFF;
font-family:Times New Roman, sans-serif; }
p { color:#000000; }
div.Divb { overflow-y: scroll;
position: sticky;
max-height: 700px;
border-radius: 10px;
top: 10px;
text-align: left; }
ul { margin: 0;
 padding: 0; }
</style>
</head>
<body>
<div class="Div2"><i><b>README</b></i></div><br><center><img src ="logo.jpg" width=250 height=100></center>
<div class="container">
<div class="Divb">
<div class="box1"><a><i>Table Of Contents</i></a><br><br><ul>
<b><li style="margin-left:20px; color: #2c4786;">The Dataframe Object</li></b>
<a href="#Dataframe" style="margin-left:40px;">Dataframe</a>
<br>
<a href="#Dataframe.readf" style="margin-left:40px;">Dataframe.readf</a>
<br>
<a href="#Dataframe.writef" style="margin-left:40px;">Dataframe.writef</a>
<br>
<a href="#Dataframe.display" style="margin-left:40px;">Dataframe.display</a>
<br>
<a href="#Dataframe.idx_dataframe" style="margin-left:40px;">Dataframe.idx_dataframe</a>
<br>
<a href="#Dataframe.name_dataframe" style="margin-left:40px;">Dataframe.name_dataframe</a>
<br>
<a href="#Dataframe.idx_colint" style="margin-left:40px;">Dataframe.idx_colint</a>
<br>
<a href="#Dataframe.name_colint" style="margin-left:40px;">Dataframe.name_colint</a>
<br>
<a href="#Dataframe.idx_colstr" style="margin-left:40px;">Dataframe.idx_colstr</a>
<br>
<a href="#Dataframe.name_colstr" style="margin-left:40px;">Dataframe.name_colstr</a>
<br>
<a href="#Dataframe.idx_colchr" style="margin-left:40px;">Dataframe.idx_colchr</a>
<br>
<a href="#Dataframe.name_colchr" style="margin-left:40px;">Dataframe.name_colchr</a>
<br>
<a href="#Dataframe.idx_matrint" style="margin-left:40px;">Dataframe.idx_matrint</a>
<br>
<a href="#Dataframe.name_matrint" style="margin-left:40px;">Dataframe.name_matrint</a>
<br>
<a href="#Dataframe.idx_matrstr" style="margin-left:40px;">Dataframe.idx_matrstr</a>
<br>
<a href="#Dataframe.name_matrstr" style="margin-left:40px;">Dataframe.name_matrstr</a>
<br>
<a href="#Dataframe.idx_matrchr" style="margin-left:40px;">Dataframe.idx_matrchr</a>
<br>
<a href="#Dataframe.name_matrchr" style="margin-left:40px;">Dataframe.name_matrchr</a>
<br>
<a href="#Dataframe.get_nrow" style="margin-left:40px;">Dataframe.get_nrow</a>
<br>
<a href="#Dataframe.get_ncol" style="margin-left:40px;">Dataframe.get_ncol</a>
<br>
<a href="#Dataframe.get_rowname" style="margin-left:40px;">Dataframe.get_rowname</a>
<br>
<a href="#Dataframe.get_colname" style="margin-left:40px;">Dataframe.get_colname</a>
<br>
<a href="#Dataframe.set_rowname" style="margin-left:40px;">Dataframe.set_rowname</a>
<br>
<a href="#Dataframe.set_colname" style="margin-left:40px;">Dataframe.set_colname</a>
<br>
<a href="#Dataframe.replace_colint" style="margin-left:40px;">Dataframe.replace_colint</a>
<br>
<a href="#Dataframe.replace_colstr" style="margin-left:40px;">Dataframe.replace_colstr</a>
<br>
<a href="#Dataframe.replace_colchr" style="margin-left:40px;">Dataframe.replace_colchr</a>
<br>
<a href="#Dataframe.add_colint" style="margin-left:40px;">Dataframe.add_colint</a>
<br>
<a href="#Dataframe.add_colstr" style="margin-left:40px;">Dataframe.add_colstr</a>
<br>
<a href="#Dataframe.add_colchr" style="margin-left:40px;">Dataframe.add_colchr</a>
<br>
<a href="#Dataframe.rm_col" style="margin-left:40px;">Dataframe.rm_col</a>
<br>
<a href="#Dataframe.rm_row" style="margin-left:40px;">Dataframe.rm_row</a>
<br>
<a href="#Dataframe.transform_inner" style="margin-left:40px;">Dataframe.transform_inner</a>
<br>
<a href="#Dataframe.transform_excluding" style="margin-left:40px;">Dataframe.transform_excluding</a>
<br>
<a href="#Dataframe.merge_inner" style="margin-left:40px;">Dataframe.merge_inner</a>
<br>
<a href="#Dataframe.merge_excluding" style="margin-left:40px;">Dataframe.merge_excluding</a>
<br>
<a href="#Dataframe.merge_excluding_both" style="margin-left:40px;">Dataframe.merge_excluding_both</a>
<br>
<a href="#Dataframe.merge_all" style="margin-left:40px;">Dataframe.merge_all</a>
<br>
</ul><br>
</div>
</div>
<div class="box2">
<h1 style="color:#2c4786;">The Dataframe Object</h1>
<h2 id="Dataframe" style="test-align: left;">Dataframe</h2>
<h3>#Usage</h3>
<div class="Div"><code>Dataframe my_dataframe</code></div>
<h3>#Description</h3>
<p>Dataframe objects supporting reading csv, with custom separator, storing columns in differents type vectors, creating a new Dataframe object on top of an already existing one specifying the rows and columns to copy, the same goes for a matrix (as <code>std::vector&lt;std::vector&lt;T&gt;&gt;</code>) and <code>std::vector&lt;T&gt;</code>. See examples.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
See_below </th><th> See below</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>See below</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.readf" style="test-align: left;">Dataframe.readf</h2>
<h3>#Usage</h3>
<div class="Div"><code>void readf(std::string &file_name, char delim = ',', bool header_name = 1, char str_context_begin = '\'', char str_context_end = '\'')</code></div>
<h3>#Description</h3>
<p>Import a csv as a Dataframe object.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
file_name </th><th> is the file_name of the csv to read</th></tr>
<tr><th>delim </th><th> is the column delimiter</th></tr>
<tr><th>header_name </th><th> is if the first row is in fact the column names</th></tr>
<tr><th>str_context_begin </th><th> is the first symbol of a quote, (to not take in count a comma as a new column if it is in a quote for example)</th></tr>
<tr><th>str_context_end </th><th> is the end symbol for a quote context</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>Dataframe obj1;</code>
<br><code>std::string file_name = "teste_dataframe.csv";</code>
<br><code>obj1.readf(file_name);</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.writef" style="test-align: left;">Dataframe.writef</h2>
<h3>#Usage</h3>
<div class="Div"><code>void writef(std::string &file_name, char delim = ',', bool header_name = 1, char str_context_bgn = '\'', char str_context_end = '\'')</code></div>
<h3>#Description</h3>
<p>Write a dataframe object into a csv file.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
file_name </th><th> is the file name to write data into</th></tr>
<tr><th>delim </th><th> is the column delimiter</th></tr>
<tr><th>header_name </th><th> 1 to write the column names, 0 else</th></tr>
<tr><th>str_context_begin </th><th> is the first symbol of a quote, (to not take in count a comma as a new column if it is in a quote for example)</th></tr>
<tr><th>str_context_end </th><th> is the end symbol for a quote context</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::string out_file = "out.csv";</code>
<br><code>obj1.writef(out_file);</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.display" style="test-align: left;">Dataframe.display</h2>
<h3>#Usage</h3>
<div class="Div"><code>void display();</code></div>
<h3>#Description</h3>
<p>Print the current dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
no </th><th> no</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>obj1.display();</code>
<br><code>&lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;</code>
<br><code>col1 col2 col3 col4 col5 col6</code>
<br><code>:0:  1    2    3    aa   5    z</code>
<br><code>:1:  6    7    8    bb   10   e</code>
<br><code>:2:  1    2    3    cc   5    h</code>
<br><code>:3:  6    7    8    uu   10   a</code>
<br><code>:4:  1    2    3    s4   -5   q</code>
<br><code>:5:  6    7    8    s9   10   p</code>
<br><code>:6:  1    2    3    a4   5    j</code>
<br><code>:7:  6    7    8    m9   10   i</code>
<br><code>:8:  6    7    8    s9   10   p</code>
<br><code>:9:  1    2    3    a4   5    j</code>
<br><code>:10: 6    7    8    m9   10   i</code>
<br><code>:11: 6    7    8    m9   10   i</code>
<br><code>:12: 6    7    8    s9   10   p</code>
<br><code>:13: 1    2    3    a4   5    j</code>
<br><code>:14: 6    7    8    m9   10   i</code>
<br>
<img style="margin-left: 20px;" height="220" width="360" src="img_dataframe.jpg"><br></div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_dataframe" style="test-align: left;">Dataframe.idx_dataframe</h2>
<h3>#Usage</h3>
<div class="Div"><code>void idx_dataframe(std::vector&lt;int&gt; &rows, std::vector&lt;int&gt; &cols, Dataframe &cur_obj)</code></div>
<h3>#Description</h3>
<p>Allow to copy a dataframe choosing rows and columns (by index) of the copied dataframe. </p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is the vector containing all the rows to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>cols </th><th> is the vector of the index of the columns to copy</th></tr>
<tr><th>cur_obj </th><th> is the dataframe that will contain all the rows and columns of the copied dataframe</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>Dataframe obj2;</code>
<br><code>std::vector&lt;int&gt; idx_rows = {-1};</code>
<br><code>std::vector&lt;int&gt; idx_cols2 = {1, 2, 3};</code>
<br><code>obj2.idx_dataframe(idx_rows, idx_cols2, obj1);</code>
<br><code></code>
<br><code>obj2.display();</code>
<br><code>    col1 col2 col3</code>
<br><code>:0:  2    3    aa</code>
<br><code>:1:  7    8    bb</code>
<br><code>:2:  2    3    cc</code>
<br><code>:3:  7    8    uu</code>
<br><code>:4:  2    3    s4</code>
<br><code>:5:  7    8    s9</code>
<br><code>:6:  2    3    a4</code>
<br><code>:7:  7    8    m9</code>
<br><code>:8:  7    8    s9</code>
<br><code>:9:  2    3    a4</code>
<br><code>:10: 7    8    m9</code>
<br><code>:11: 7    8    m9</code>
<br><code>:12: 7    8    s9</code>
<br><code>:13: 2    3    a4</code>
<br><code>:14: 7    8    m9</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_dataframe" style="test-align: left;">Dataframe.name_dataframe</h2>
<h3>#Usage</h3>
<div class="Div"><code>void name_dataframe(std::vector&lt;int&gt; &rows, std::vector&lt;int&gt; &name_cols, Dataframe &cur_obj)</code></div>
<h3>#Description</h3>
<p>Allow to copy a dataframe choosing rows and columns (by name) of the copied dataframe. </p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is the vector containing all the rows to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>cols </th><th> is the vector of the name of the columns to copy</th></tr>
<tr><th>cur_obj </th><th> is the dataframe that will contain all the rows and columns of the copied dataframe</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>Dataframe obj2;</code>
<br><code>std::vector&lt;int&gt; idx_rows = {-1};</code>
<br><code>std::vector&lt;std::string&gt; idx_cols2 = {"col2", "col3", "col3"};</code>
<br><code>obj2.name_dataframe(idx_rows, idx_cols2, obj1);</code>
<br><code></code>
<br><code>obj2.display();</code>
<br><code>    col1 col2 col3</code>
<br><code>:0:  2    3    aa</code>
<br><code>:1:  7    8    bb</code>
<br><code>:2:  2    3    cc</code>
<br><code>:3:  7    8    uu</code>
<br><code>:4:  2    3    s4</code>
<br><code>:5:  7    8    s9</code>
<br><code>:6:  2    3    a4</code>
<br><code>:7:  7    8    m9</code>
<br><code>:8:  7    8    s9</code>
<br><code>:9:  2    3    a4</code>
<br><code>:10: 7    8    m9</code>
<br><code>:11: 7    8    m9</code>
<br><code>:12: 7    8    s9</code>
<br><code>:13: 2    3    a4</code>
<br><code>:14: 7    8    m9</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_colint" style="test-align: left;">Dataframe.idx_colint</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void idx_colint(std::vector&lt;int&gt; rows, unsigned int x, std::vector&lt;T&gt; &rtn_v)</code></div>
<h3>#Description</h3>
<p>Allow to copy a int, unsigned int , bool or double column as a vector&lt;T&gt;, by column index.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x </th><th> is the index of the column to copy</th></tr>
<tr><th>rtn_v </th><th> is the vector that will contain the column to copy</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;int&gt; currows = {1, 0, 1};</code>
<br><code>std::vector&lt;unsigned int&gt; outv = {};</code>
<br><code>obj1.idx_colint(currows, 2, outv);</code>
<br><code>print_nvec(outv);</code>
<br><code>:0: 8 3 8</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_colint" style="test-align: left;">Dataframe.name_colint</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void name_colint(std::vector&lt;int&gt; rows, std::string colname, std::vector&lt;T&gt; &rtn_v)</code></div>
<h3>#Description</h3>
<p>Allow to copy a int, unsigned int , bool or double column as a vector&lt;T&gt;, by column name.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x </th><th> is the name of the column to copy</th></tr>
<tr><th>rtn_v </th><th> is the vector that will contain the column to copy</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;int&gt; currows = {1, 0, 1};</code>
<br><code>std::vector&lt;unsigned int&gt; outv = {};</code>
<br><code>obj1.idx_colint(currows, "col2", outv);</code>
<br><code>print_nvec(outv);</code>
<br><code>:0: 8 3 8</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_colstr" style="test-align: left;">Dataframe.idx_colstr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void idx_colstr(std::vector&lt;int&gt; rows, unsigned int x, std::vector&lt;std::string&gt; &rtn_v)</code></div>
<h3>#Description</h3>
<p>Allow to copy a std::string column as a vector&lt;std::string&gt;, by column index.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x </th><th> is the index of the column to copy</th></tr>
<tr><th>rtn_v </th><th> is the vector that will contain the column to copy</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::string&gt; outv2 = {};</code>
<br><code>obj1.idx_colstr(currows, 3, outv2);</code>
<br><code>print_svec(outv2);</code>
<br><code>:0: bb aa bb</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_colstr" style="test-align: left;">Dataframe.name_colstr</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void name_colint(std::vector&lt;int&gt; rows, std::string colname, std::vector&lt;T&gt; &rtn_v)</code></div>
<h3>#Description</h3>
<p>Allow to copy a int, unsigned int , bool or double column as a vector&lt;std::string&gt;, by column name.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x </th><th> is the name of the column to copy</th></tr>
<tr><th>rtn_v </th><th> is the vector that will contain the column to copy</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::string&gt; outv2 = {};</code>
<br><code>obj1.name_colstr(currows, "col4", outv2);</code>
<br><code>print_svec(outv2);</code>
<br><code>:0: bb aa bb</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_colchr" style="test-align: left;">Dataframe.idx_colchr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void idx_colchr(std::vector&lt;int&gt; rows, unsigned int x, std::vector&lt;char&gt; &rtn_v)</code></div>
<h3>#Description</h3>
<p>Allow to copy a char column as a vector&lt;char&gt;, by column index.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x </th><th> is the index of the column to copy</th></tr>
<tr><th>rtn_v </th><th> is the vector that will contain the column to copy</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;char&gt; outv3 = {};</code>
<br><code>obj1.idx_colchr(currows, 5, outv3);</code>
<br><code>for (char i : outv3) {</code>
<br><code>  std::cout &lt;&lt; i &lt;&lt; " ";</code>
<br><code>};</code>
<br><code>std::cout &lt;&lt; "\n";</code>
<br><code>e z e</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_colchr" style="test-align: left;">Dataframe.name_colchr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void name_colchr(std::vector&lt;int&gt; rows, std::string colname, std::vector&lt;char&gt; &rtn_v)</code></div>
<h3>#Description</h3>
<p>Allow to copy a char column as a vector&lt;char&gt;, by column name.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x </th><th> is the name of the column to copy</th></tr>
<tr><th>rtn_v </th><th> is the vector that will contain the column to copy</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;char&gt; outv3 = {};</code>
<br><code>obj1.name_colchr(currows, "col6", outv3);</code>
<br><code>for (char i : outv3) {</code>
<br><code>  std::cout &lt;&lt; i &lt;&lt; " ";</code>
<br><code>};</code>
<br><code>std::cout &lt;&lt; "\n";</code>
<br><code>e z e</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_matrint" style="test-align: left;">Dataframe.idx_matrint</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void idx_matrint(std::vector&lt;int&gt; rows, std::vector&lt;unsigned int&gt; x_v, std::vector&lt;std::vector&lt;T&gt;&gt; &rtn_matr)</code></div>
<h3>#Description</h3>
<p>Allow to copy a set of columns that are same type (int, unsigned int, bool or double) as a <code> std::vector&lt;std::vector&lt;T&gt;&gt; </code>, by column index.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code> {-1} </code>) for all</th></tr>
<tr><th>x_v </th><th> is the vector containing the indices of the column to copy</th></tr>
<tr><th>rtn_matr </th><th> is the matrix that will contain all the columns copyed</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::vector&lt;unsigned int&gt;&gt; out_matr = {};</code>
<br><code>std::vector&lt;unsigned int&gt; idx_cols = {1, 0, 2, 2};</code>
<br><code>obj1.idx_matrint(currows, idx_cols, out_matr);</code>
<br><code>print_nmatr(out_matr);</code>
<br><code>                  [0]               [1]               [2]               [3]</code>
<br><code>:0:                 7                 6                 8                 8</code>
<br><code>:1:                 2                 1                 3                 3</code>
<br><code>:2:                 7                 6                 8                 8</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_matrint" style="test-align: left;">Dataframe.name_matrint</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void name_matrint(std::vector&lt;int&gt; rows, std::vector&lt;std::string&gt; x_v, std::vector&lt;std::vector&lt;T&gt;&gt; &rtn_matr)</code></div>
<h3>#Description</h3>
<p>Allow to copy a set of columns that are same type (int, unsigned int, bool or double) as a <code>std::vector&lt;std::vector&lt;T&gt;&gt;</code>, by column name.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x_v </th><th> is the vector containing the names of the column to copy</th></tr>
<tr><th>rtn_matr </th><th> is the matrix that will contain all the columns copyed</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::vector&lt;unsigned int&gt;&gt; out_matr = {};</code>
<br><code>std::vector&lt;std::string&gt; idx_vec2 = {"col1", "col2", "col3"};</code>
<br><code>obj1.name_matrint(currows, idx_vec2, out_matr);</code>
<br><code>print_nmatr(out_matr);</code>
<br><code>                  [0]               [1]               [2]</code>
<br><code>:0:                 6                 7                 8</code>
<br><code>:1:                 1                 2                 3</code>
<br><code>:2:                 6                 7                 8</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_matrstr" style="test-align: left;">Dataframe.idx_matrstr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void idx_matrstr(std::vector&lt;int&gt; rows, std::vector&lt;unsigned int&gt; x_v, std::vector&lt;std::vector&lt;std::string&gt;&gt; &rtn_matr)</code></div>
<h3>#Description</h3>
<p>Allow to copy a set of columns that are <code>std::string</code> type as a <code>std::vector&lt;std::vector&lt;std::string&gt;&gt;</code>, by column index.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x_v </th><th> is the vector containing the indices of the column to copy</th></tr>
<tr><th>rtn_matr </th><th> is the matrix that will contain all the columns copyed</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::vector&lt;std::string&gt;&gt; out_matr2 = {};</code>
<br><code>std::vector&lt;unsigned int&gt; idx_cols = {3};</code>
<br><code>obj1.idx_matrstr(currows, idx_cols, out_matr2);</code>
<br><code>print_smatr(out_matr2);</code>
<br><code>                    [0]</code>
<br><code>:0:                   bb</code>
<br><code>:1:                   aa</code>
<br><code>:2:                   bb</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_matrstr" style="test-align: left;">Dataframe.name_matrstr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void name_matrstr(std::vector&lt;int&gt; rows, std::vector&lt;std::string&gt; x_v, std::vector&lt;std::vector&lt;std::string&gt;&gt; &rtn_matr)</code></div>
<h3>#Description</h3>
<p>Allow to copy a set of columns that are <code>std::string</code> type as a <code>std::vector&lt;std::vector&lt;std::string&gt;&gt;</code>, by column name.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x_v </th><th> is the vector containing the names of the column to copy</th></tr>
<tr><th>rtn_matr </th><th> is the matrix that will contain all the columns copyed</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::vector&lt;std::string&gt;&gt; out_matr2 = {};</code>
<br><code>std::vector&lt;std::string&gt; idx_vec2 = {"col4"};</code>
<br><code>obj1.name_matrstr(currows, idx_vec2, out_matr2);</code>
<br><code>print_smatr(out_matr2);</code>
<br><code>                    [0]</code>
<br><code>:0:                   bb</code>
<br><code>:1:                   aa</code>
<br><code>:2:                   bb</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.idx_matrchr" style="test-align: left;">Dataframe.idx_matrchr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void idx_matrchr(std::vector&lt;int&gt; rows, std::vector&lt;unsigned int&gt; x_v, std::vector&lt;std::vector&lt;char&gt;&gt; &rtn_matr)</code></div>
<h3>#Description</h3>
<p>Allow to copy a set of columns that are <code>char</code> type as a <code>std::vector&lt;std::vector&lt;char&gt;&gt;</code>, by column index.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x_v </th><th> is the vector containing the indices of the column to copy</th></tr>
<tr><th>rtn_matr </th><th> is the matrix that will contain all the columns copyed</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::vector&lt;char&gt;&gt; out_matr3 = {};</code>
<br><code>std::vector&lt;unsigned int&gt; idx_cols = {5};</code>
<br><code>obj1.idx_matrchr(currows, idx_cols, out_matr3);</code>
<br><code>print_smatr(out_matr3);</code>
<br><code>                    [0]</code>
<br><code>:0:                    e</code>
<br><code>:1:                    z</code>
<br><code>:2:                    e</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.name_matrchr" style="test-align: left;">Dataframe.name_matrchr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void name_matrchr(std::vector&lt;int&gt; rows, std::vector&lt;std::string&gt; x_v, std::vector&lt;std::vector&lt;char&gt;&gt; &rtn_matr)</code></div>
<h3>#Description</h3>
<p>Allow to copy a set of columns that are <code>char</code> type as a <code>std::vector&lt;std::vector&lt;char&gt;&gt;</code>, by column name.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
rows </th><th> is a vector containing the row indices to copy (<code>{-1}</code>) for all</th></tr>
<tr><th>x_v </th><th> is the vector containing the names of the column to copy</th></tr>
<tr><th>rtn_matr </th><th> is the matrix that will contain all the columns copyed</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;char&gt; out_matr3 = {};</code>
<br><code>std::vector&lt;std::string&gt; idx_vec2 = {"col6"};</code>
<br><code>obj1.name_matrchr(currows, idx_vec2, out_matr3);</code>
<br><code>print_smatr(out_matr3);</code>
<br><code>                    [0]</code>
<br><code>:0:                    e</code>
<br><code>:1:                    z</code>
<br><code>:2:                    e</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.get_nrow" style="test-align: left;">Dataframe.get_nrow</h2>
<h3>#Usage</h3>
<div class="Div"><code>unsigned int get_nrow();</code></div>
<h3>#Description</h3>
<p>Returns the number of rows for the associated dataframe.</p>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>unsigned int nrow = obj1.get_nrow();</code>
<br><code>15</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.get_ncol" style="test-align: left;">Dataframe.get_ncol</h2>
<h3>#Usage</h3>
<div class="Div"><code>unsigned int get_ncol();</code></div>
<p>Returns the number of columns for the associated dataframe.</p>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>unsigned int ncol = obj1.get_ncol();</code>
<br><code>6</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.get_rowname" style="test-align: left;">Dataframe.get_rowname</h2>
<h3>#Usage</h3>
<div class="Div"><code>std::vector&lt;std::string&gt; get_rowname();</code></div>
<p>Returns the rowname of the associated dataframe.</p>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::string&gt; row_names = obj1.get_rowname();</code>
<br><code>nothing becuase obj1 has no rownames</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.get_colname" style="test-align: left;">Dataframe.get_colname</h2>
<h3>#Usage</h3>
<div class="Div"><code>std::vector&lt;std::string&gt; get_colname();</code></div>
<p>Returns the colname of the associated dataframe.</p>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::string&gt; col_names = obj1.get_colname();</code>
<br><code>col1 col2 col3 col4 col5 col6</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.set_rowname" style="test-align: left;">Dataframe.set_rowname</h2>
<h3>#Usage</h3>
<div class="Div"><code>void set_rowname(std::vector&lt;std::string&gt; &x);</code></div>
<p>Set rowname to the associated dataframe.</p>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::string&gt; row_names = {"n1", "n2", "n3"..."n15"};</code>
<br><code>obj1.set_rowname(row_names);</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.set_colname" style="test-align: left;">Dataframe.set_colname</h2>
<h3>#Usage</h3>
<div class="Div"><code>void set_colname(std::vector&lt;std::string&gt; &x);</code></div>
<p>Set colname to the associated dataframe.</p>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;std::string&gt; col_names = {"col1", "col2", "col3", "col4", </code>
<br><code>"col5", "col6"};</code>
<br><code>obj1.set_colname();</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.replace_colint" style="test-align: left;">Dataframe.replace_colint</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void replace_colint(std::vector&lt;T&gt; &x, unsigned int &colnb)</code></div>
<p>Replace a int, unsigned int, bool or double column of the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
x </th><th> is the column (as vector) that will replace the dataframe column</th></tr>
<tr><th>colnb </th><th> is the index of the column to replace</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; rpl_col = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, </code>
<br><code>                                      10, 11, 12, 13, 14};</code>
<br><code>unsigned int col = 0;</code>
<br><code>obj1.replace_colint(rpl_col, col);</code>
<br><code>obj1.display();</code>
<br><code>     &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;</code>
<br><code>     col1   col2   col3   col4  col5  col6</code>
<br><code> :0:  0      2      3      aa    5     z</code>
<br><code> :1:  1      7      8      bb    10    e</code>
<br><code> :2:  2      2      3      cc    5     h</code>
<br><code> :3:  3      7      8      uu    10    a</code>
<br><code> :4:  4      2      3      s4    -5    q</code>
<br><code> :5:  5      7      8      s9    10    p</code>
<br><code> :6:  6      2      3      a4    5     j</code>
<br><code> :7:  7      7      8      m9    10    i</code>
<br><code> :8:  8      7      8      s9    10    p</code>
<br><code> :9:  9      2      3      a4    5     j</code>
<br><code> :10: 10     7      8      m9    10    i</code>
<br><code> :11: 11     7      8      m9    10    i</code>
<br><code> :12: 12     7      8      s9    10    p</code>
<br><code> :13: 13     2      3      NA    5     j</code>
<br><code> :14: 14     7      8      m9    10    i</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.replace_colstr" style="test-align: left;">Dataframe.replace_colstr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void replace_colstr(std::vector&lt;std::string&gt; &x, unsigned int &colnb)</code></div>
<h3>#Description</h3>
<p>Replace a string column of the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
x </th><th> is the column (as vector) that will replace the dataframe column</th></tr>
<tr><th>colnb </th><th> is the index of the column to replace</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code></code>
<br><code>std::vector&lt;std::string&gt; rpl_col = {"0", "1", "2", "3", "4", "5", "6", </code>
<br><code>                                        "7", "8", "9", </code>
<br><code>                                        "10", "11", "12", "13", "14"};</code>
<br><code>unsigned int col = 3;</code>
<br><code>obj1.replace_colstr(rpl_col, col);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;</code>
<br><code>    col1   col2   col3   col4  col5  col6</code>
<br><code>:0:  1      2      3      0     5     z</code>
<br><code>:1:  6      7      8      1     10    e</code>
<br><code>:2:  1      2      3      2     5     h</code>
<br><code>:3:  6      7      8      3     10    a</code>
<br><code>:4:  1      2      3      4     -5    q</code>
<br><code>:5:  6      7      8      5     10    p</code>
<br><code>:6:  1      2      3      6     5     j</code>
<br><code>:7:  6      7      8      7     10    i</code>
<br><code>:8:  6      7      8      8     10    p</code>
<br><code>:9:  1      2      3      9     5     j</code>
<br><code>:10: 6      7      8      10    10    i</code>
<br><code>:11: 6      7      8      11    10    i</code>
<br><code>:12: 6      7      8      12    10    p</code>
<br><code>:13: 1      2      3      13    5     j</code>
<br><code>:14: 6      7      8      14    10    i</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.replace_colchr" style="test-align: left;">Dataframe.replace_colchr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void replace_colchr(std::vector&lt;char&gt; &x, unsigned int &colnb)</code></div>
<h3>#Description</h3>
<p>Replace a string column of the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
x </th><th> is the column (as vector) that will replace the dataframe column</th></tr>
<tr><th>colnb </th><th> is the index of the column to replace</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code></code>
<br><code>std::vector&lt;char&gt; rpl_col = {'c', 'c', 'c', 'c', 'c', 'c', 'c', </code>
<br><code>                                      'c', 'c', 'c', </code>
<br><code>                                      'b', 'b', 'v', 'v', 'v'};</code>
<br><code>unsigned int col = 5;</code>
<br><code>obj1.replace_colchr(rpl_col, col);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;</code>
<br><code>    col1   col2   col3   col4  col5  col6</code>
<br><code>:0:  1      2      3      aa    5     c</code>
<br><code>:1:  6      7      8      bb    10    c</code>
<br><code>:2:  1      2      3      cc    5     c</code>
<br><code>:3:  6      7      8      uu    10    c</code>
<br><code>:4:  1      2      3      s4    -5    c</code>
<br><code>:5:  6      7      8      s9    10    c</code>
<br><code>:6:  1      2      3      a4    5     c</code>
<br><code>:7:  6      7      8      m9    10    c</code>
<br><code>:8:  6      7      8      s9    10    c</code>
<br><code>:9:  1      2      3      a4    5     c</code>
<br><code>:10: 6      7      8      m9    10    b</code>
<br><code>:11: 6      7      8      m9    10    b</code>
<br><code>:12: 6      7      8      s9    10    v</code>
<br><code>:13: 1      2      3      NA    5     v</code>
<br><code>:14: 6      7      8      m9    10    v</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.add_colint" style="test-align: left;">Dataframe.add_colint</h2>
<h3>#Usage</h3>
<div class="Div"><code>template &lt;typename T&gt; void add_colint(std::vector&lt;T&gt; &x, std::string name = "NA")</code></div>
<h3>#Description</h3>
<p>Add a column int, unsigned int, bool or double type to the associated dataframe</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
x </th><th> is the column to add</th></tr>
<tr><th>name </th><th> is the column to add name</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;unsigned int&gt; rpl_col = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, </code>
<br><code>                                      10, 11, 12, 13, 14};</code>
<br><code>obj1.add_colint(rpl_col);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt; &lt;uint&gt;</code>
<br><code>    col1   col2   col3   col4  col5  col6   NA</code>
<br><code>:0:  1      2      3      aa    5     z      0</code>
<br><code>:1:  6      7      8      bb    10    e      1</code>
<br><code>:2:  1      2      3      cc    5     h      2</code>
<br><code>:3:  6      7      8      uu    10    a      3</code>
<br><code>:4:  1      2      3      s4    -5    q      4</code>
<br><code>:5:  6      7      8      s9    10    p      5</code>
<br><code>:6:  1      2      3      a4    5     j      6</code>
<br><code>:7:  6      7      8      m9    10    i      7</code>
<br><code>:8:  6      7      8      s9    10    p      8</code>
<br><code>:9:  1      2      3      a4    5     j      9</code>
<br><code>:10: 6      7      8      m9    10    i      10</code>
<br><code>:11: 6      7      8      m9    10    i      11</code>
<br><code>:12: 6      7      8      s9    10    p      12</code>
<br><code>:13: 1      2      3      NA    5     j      13</code>
<br><code>:14: 6      7      8      m9    10    i      14</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.add_colstr" style="test-align: left;">Dataframe.add_colstr</h2>
<h3>#Usage</h3>
<div class="Div"><code>void add_colstr(std::vector&lt;std::string&gt; &x, std::string name = "NA")</code></div>
<h3>#Description</h3>
<p>Add a column string type to the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
x </th><th> is the column to add</th></tr>
<tr><th>name </th><th> is the column to add name</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code></code>
<br><code>std::vector&lt;std::string&gt; rpl_col = {"0", "1", "2", "3", "4", "5", "6", "7", "8", "9", </code>
<br><code>                                      "10", "11", "12", "13", "14"};</code>
<br><code>obj1.add_colstr(rpl_col);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt; &lt;str&gt;</code>
<br><code>    col1   col2   col3   col4  col5  col6   NA</code>
<br><code>:0:  1      2      3      aa    5     z      0</code>
<br><code>:1:  6      7      8      bb    10    e      1</code>
<br><code>:2:  1      2      3      cc    5     h      2</code>
<br><code>:3:  6      7      8      uu    10    a      3</code>
<br><code>:4:  1      2      3      s4    -5    q      4</code>
<br><code>:5:  6      7      8      s9    10    p      5</code>
<br><code>:6:  1      2      3      a4    5     j      6</code>
<br><code>:7:  6      7      8      m9    10    i      7</code>
<br><code>:8:  6      7      8      s9    10    p      8</code>
<br><code>:9:  1      2      3      a4    5     j      9</code>
<br><code>:10: 6      7      8      m9    10    i      10</code>
<br><code>:11: 6      7      8      m9    10    i      11</code>
<br><code>:12: 6      7      8      s9    10    p      12</code>
<br><code>:13: 1      2      3      NA    5     j      13</code>
<br><code>:14: 6      7      8      m9    10    i      14</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.add_colchr" style="test-align: left;">Dataframe.add_colchr</h2>
<h3>#Usage</h3>
<div class="Div"><code>add_colchr(std::vector&lt;char&gt; &x, std::string name = "NA")</code></div>
<h3>#Description</h3>
<p>Add a column char type to the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
x </th><th> is the column to add</th></tr>
<tr><th>name </th><th> is the column to add name</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;char&gt; rpl_col = {'c', 'c', 'c', 'c', 'c', 'c', 'c', </code>
<br><code>                                      'c', 'c', 'c', </code>
<br><code>                                      'b', 'b', 'v', 'v', 'v'};</code>
<br><code>obj1.add_colchr(rpl_col);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt; &lt;char&gt;</code>
<br><code>    col1   col2   col3   col4  col5  col6   NA</code>
<br><code>:0:  1      2      3      aa    5     z      c</code>
<br><code>:1:  6      7      8      bb    10    e      c</code>
<br><code>:2:  1      2      3      cc    5     h      c</code>
<br><code>:3:  6      7      8      uu    10    a      c</code>
<br><code>:4:  1      2      3      s4    -5    q      c</code>
<br><code>:5:  6      7      8      s9    10    p      c</code>
<br><code>:6:  1      2      3      a4    5     j      c</code>
<br><code>:7:  6      7      8      m9    10    i      c</code>
<br><code>:8:  6      7      8      s9    10    p      c</code>
<br><code>:9:  1      2      3      a4    5     j      c</code>
<br><code>:10: 6      7      8      m9    10    i      b</code>
<br><code>:11: 6      7      8      m9    10    i      b</code>
<br><code>:12: 6      7      8      s9    10    p      v</code>
<br><code>:13: 1      2      3      NA    5     j      v</code>
<br><code>:14: 6      7      8      m9    10    i      v</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.rm_col" style="test-align: left;">Dataframe.rm_col</h2>
<h3>#Usage</h3>
<div class="Div"><code>void rm_col(std::vector&lt;unsigned int&gt; &nbcolv)</code></div>
<h3>#Description</h3>
<p>Removes columns from associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
nbcolv </th><th> is a vector containing all the indices of the columns to erase from the associated dataframe. The indices must be sorted descendly.</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 1};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;str&gt;  &lt;char&gt;</code>
<br><code>    col1   col3   col4   col6</code>
<br><code>:0:  1      3      aa     z</code>
<br><code>:1:  6      8      bb     e</code>
<br><code>:2:  1      3      cc     h</code>
<br><code>:3:  6      8      uu     a</code>
<br><code>:4:  1      3      s4     q</code>
<br><code>:5:  6      8      s9     p</code>
<br><code>:6:  1      3      a4     j</code>
<br><code>:7:  6      8      m9     i</code>
<br><code>:8:  6      8      s9     p</code>
<br><code>:9:  1      3      a4     j</code>
<br><code>:10: 6      8      m9     i</code>
<br><code>:11: 6      8      m9     i</code>
<br><code>:12: 6      8      s9     p</code>
<br><code>:13: 1      3      NA     j</code>
<br><code>:14: 6      8      m9     i</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.rm_row" style="test-align: left;">Dataframe.rm_row</h2>
<h3>#Usage</h3>
<div class="Div"><code>void rm_col(std::vector&lt;unsigned int&gt; &nbcolv)</code></div>
<h3>#Description</h3>
<p>Removes rows from associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
nbcolv </th><th> is a vector containing all the indices of the rows to erase from the associated dataframe. The indices must be sorted descendly.</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>// after reading teste_dataframe.csv as obj1</code>
<br><code>std::vector&lt;unsigned int&gt; rowv = {4, 1};</code>
<br><code>obj1.rm_row(rowv);</code>
<br><code>obj1.display();</code>
<br><code>    &lt;uint&gt; &lt;uint&gt; &lt;uint&gt; &lt;str&gt; &lt;int&gt; &lt;char&gt;</code>
<br><code>    col1   col2   col3   col4  col5  col6</code>
<br><code>:0:  1      2      3      aa    5     z</code>
<br><code>:1:  1      2      3      cc    5     h</code>
<br><code>:2:  6      7      8      uu    10    a</code>
<br><code>:3:  6      7      8      s9    10    p</code>
<br><code>:4:  1      2      3      a4    5     j</code>
<br><code>:5:  6      7      8      m9    10    i</code>
<br><code>:6:  6      7      8      s9    10    p</code>
<br><code>:7:  1      2      3      a4    5     j</code>
<br><code>:8:  6      7      8      m9    10    i</code>
<br><code>:9:  6      7      8      m9    10    i</code>
<br><code>:10: 6      7      8      s9    10    p</code>
<br><code>:11: 1      2      3      NA    5     j</code>
<br><code>:12: 6      7      8      m9    10    i</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.transform_inner" style="test-align: left;">Dataframe.transform_inner</h2>
<h3>#Usage</h3>
<div class="Div"><code>void transform_inner(Dataframe &cur_obj, unsigned int &in_col, unsigned int &ext_col)</code></div>
<h3>#Description</h3>
<p>Applies a inner join on the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
cur_obj </th><th> is the other dataframe used for inner join</th></tr>
<tr><th>in_col </th><th> is the index of the column representing the key (primary) of the associated dataframe</th></tr>
<tr><th>ext_col </th><th> is the index of the column representing the key (foreign) of the other dataframe used for the inner join</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code></code>
<br><code>Dataframe obj1, obj2;</code>
<br><code>std::string filename = "outb.csv";</code>
<br><code>obj1.readf(filename);</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 3, 2};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code></code>
<br><code>std::string f2 = "outb2.csv";</code>
<br><code>obj2.readf(f2);</code>
<br><code></code>
<br><code>unsigned int col1 = 0;</code>
<br><code>unsigned int col2 = 0;</code>
<br><code></code>
<br><code>obj1.transform_inner(obj2, col1, col2);</code>
<br><code>obj1.display();</code>
<br><code> &lt;str&gt; &lt;uint&gt;</code>
<br><code>    col1  col2</code>
<br><code>:0:  id1   1</code>
<br><code>:1:  id2   6</code>
<br><code>:2:  id4   6</code>
<br><code>:3:  id5   1</code>
<br><code>:4:  id6   6</code>
<br><code>:5:  id7   1</code>
<br><code>:6:  id8   6</code>
<br><code>:7:  id9   6</code>
<br><code>:8:  id11  6</code>
<br><code>:9:  id12  6</code>
<br><code>:10: id14  1</code>
<br><code>:11: id15  6</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.transform_excluding" style="test-align: left;">Dataframe.transform_excluding</h2>
<h3>#Usage</h3>
<div class="Div"><code>void transform_excluding(Dataframe &cur_obj, unsigned int &in_col, unsigned int &ext_col)</code></div>
<h3>#Description</h3>
<p>Applies a excluding join on the associated dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
cur_obj </th><th> is the other dataframe used for the excluding join</th></tr>
<tr><th>in_col </th><th> is the index of the column representing the key (primary) of the associated dataframe</th></tr>
<tr><th>ext_col </th><th> is the index of the column representing the key (foreign) of the other dataframe used for the excluding join</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code></code>
<br><code>Dataframe obj1, obj2;</code>
<br><code>std::string filename = "outb.csv";</code>
<br><code>obj1.readf(filename);</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 3, 2};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code></code>
<br><code>std::string f2 = "outb2.csv";</code>
<br><code>obj2.readf(f2);</code>
<br><code></code>
<br><code>unsigned int col1 = 0;</code>
<br><code>unsigned int col2 = 0;</code>
<br><code></code>
<br><code>obj1.transform_excluding(obj2, col1, col2);</code>
<br><code>obj1.display();</code>
<br><code>   &lt;str&gt; &lt;uint&gt;</code>
<br><code>   col1  col2</code>
<br><code>:0: id3   1</code>
<br><code>:1: id10  1</code>
<br><code>:2: id13  6</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.merge_inner" style="test-align: left;">Dataframe.merge_inner</h2>
<h3>#Usage</h3>
<div class="Div"><code>void merge_inner(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)</code></div>
<h3>#Description</h3>
<p>Performs a inner join on a newly created dataframe.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
obj1 </th><th> is the first dataframe</th></tr>
<tr><th>obj2 </th><th> is the second dataframe</th></tr>
<tr><th>colname </th><th> 1 to give the column names to the newly created dataframe</th></tr>
<tr><th>key1 </th><th> is the index of the first dataframe column as primary key</th></tr>
<tr><th>key1 </th><th> is the index of the first dataframe column as foreign key</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code></code>
<br><code>Dataframe obj1, obj2, obj3;</code>
<br><code>std::string filename = "outb.csv";</code>
<br><code>obj1.readf(filename);</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 3, 2};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code></code>
<br><code>std::string f2 = "outb2.csv";</code>
<br><code>obj2.readf(f2);</code>
<br><code></code>
<br><code>unsigned int col1 = 0;</code>
<br><code>unsigned int col2 = 0;</code>
<br><code></code>
<br><code>obj3.merge_inner(obj1, obj2, 1, col1, col2);</code>
<br><code>obj3.display();</code>
<br><code>    &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;</code>
<br><code></code>
<br><code>:0:  id1   1      id1   2      3</code>
<br><code>:1:  id2   6      id2   7      8</code>
<br><code>:2:  id4   6      id4   7      8</code>
<br><code>:3:  id5   1      id5   2      3</code>
<br><code>:4:  id6   6      id6   7      8</code>
<br><code>:5:  id7   1      id7   2      3</code>
<br><code>:6:  id8   6      id8   2      3</code>
<br><code>:7:  id9   6      id9   7      8</code>
<br><code>:8:  id11  6      id11  7      8</code>
<br><code>:9:  id12  6      id12  7      8</code>
<br><code>:10: id14  1      id14  7      8</code>
<br><code>:11: id15  6      id15  2      3</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.merge_excluding" style="test-align: left;">Dataframe.merge_excluding</h2>
<h3>#Usage</h3>
<div class="Div"><code>void merge_excluding(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)</code></div>
<h3>#Description</h3>
<p>Performs a left excluding join to the associated dataframe (newly created). The first dataframe as argument is considered as the left one.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
obj1 </th><th> is the left dataframe</th></tr>
<tr><th>obj2 </th><th> is the right dataframe</th></tr>
<tr><th>colname </th><th> 1 to give the column names to the newly created dataframe</th></tr>
<tr><th>key1 </th><th> is the index of the column of the left dataframe</th></tr>
<tr><th>key2 </th><th> is the index of the column of the right dataframe</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>Dataframe obj1, obj2, obj3;</code>
<br><code>std::string filename = "outb.csv";</code>
<br><code>obj1.readf(filename);</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 3, 2};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code></code>
<br><code>std::string f2 = "outb2.csv";</code>
<br><code>obj2.readf(f2);</code>
<br><code></code>
<br><code>unsigned int col1 = 0;</code>
<br><code>unsigned int col2 = 0;</code>
<br><code></code>
<br><code>obj3.merge_excluding(obj1, obj2, 1, col1, col2);</code>
<br><code>obj3.display();</code>
<br><code>   &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;</code>
<br><code></code>
<br><code>:0: id3   1      NA    NA     NA</code>
<br><code>:1: id10  1      NA    NA     NA</code>
<br><code>:2: id13  6      NA    NA     NA</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.merge_excluding_both" style="test-align: left;">Dataframe.merge_excluding_both</h2>
<h3>#Usage</h3>
<div class="Div"><code>void merge_excluding_both(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)</code></div>
<h3>#Description</h3>
<p>Performs a full excluding join to the associated dataframe (newly created). The first dataframe as argument is considered as the left one.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
obj1 </th><th> is the left dataframe</th></tr>
<tr><th>obj2 </th><th> is the right dataframe</th></tr>
<tr><th>colname </th><th> 1 to give the column names to the newly created dataframe</th></tr>
<tr><th>key1 </th><th> is the index of the column of the left dataframe</th></tr>
<tr><th>key2 </th><th> is the index of the column of the right dataframe</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>Dataframe obj1, obj2, obj3;</code>
<br><code>std::string filename = "outb.csv";</code>
<br><code>obj1.readf(filename);</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 3, 2};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code></code>
<br><code>std::string f2 = "outb2.csv";</code>
<br><code>obj2.readf(f2);</code>
<br><code></code>
<br><code>unsigned int col1 = 0;</code>
<br><code>unsigned int col2 = 0;</code>
<br><code></code>
<br><code>obj3.merge_excluding_both(obj1, obj2, 1, col1, col2);</code>
<br><code>obj3.display();</code>
<br><code>   &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;</code>
<br><code></code>
<br><code>:0: id3   1      NA    NA     NA</code>
<br><code>:1: id10  1      NA    NA     NA</code>
<br><code>:2: id13  6      NA    NA     NA</code>
<br><code>:3: NA    NA     id119 7      8</code>
</div>
<br>
<hr class="hr">
<h2 id="Dataframe.merge_all" style="test-align: left;">Dataframe.merge_all</h2>
<h3>#Usage</h3>
<div class="Div"><code>void merge_all(Dataframe &obj1, Dataframe &obj2, bool colname, unsigned int &key1, unsigned int &key2)</code></div>
<h3>#Description</h3>
<p>Performs a full join to the associated dataframe (newly created). The first dataframe as argument is considered as the left one.</p>
<h3>#Arguments</h3>
<table><tr><th>Name</th><th>Definition</th></tr><tr><th>
obj1 </th><th> is the left dataframe</th></tr>
<tr><th>obj2 </th><th> is the right dataframe</th></tr>
<tr><th>colname </th><th> 1 to give the column names to the newly created dataframe</th></tr>
<tr><th>key1 </th><th> is the index of the column of the left dataframe</th></tr>
<tr><th>key2 </th><th> is the index of the column of the right dataframe</th></tr>
</table>
<br>
<h3>#Example(s)</h3>
<div class = "Div"><code>Dataframe obj1, obj2, obj3;</code>
<br><code>std::string filename = "outb.csv";</code>
<br><code>obj1.readf(filename);</code>
<br><code></code>
<br><code>std::vector&lt;unsigned int&gt; colv = {4, 3, 2};</code>
<br><code>obj1.rm_col(colv);</code>
<br><code></code>
<br><code>std::string f2 = "outb2.csv";</code>
<br><code>obj2.readf(f2);</code>
<br><code></code>
<br><code>unsigned int col1 = 0;</code>
<br><code>unsigned int col2 = 0;</code>
<br><code></code>
<br><code>obj3.merge_all(obj1, obj2, 1, col1, col2);</code>
<br><code>obj3.display();</code>
<br><code>    &lt;str&gt; &lt;uint&gt; &lt;str&gt; &lt;uint&gt; &lt;uint&gt;</code>
<br><code></code>
<br><code>:0:  id3   1      NA    NA     NA</code>
<br><code>:1:  id10  1      NA    NA     NA</code>
<br><code>:2:  id13  6      NA    NA     NA</code>
<br><code>:3:  NA    NA     id119 7      8</code>
<br><code>:4:  id1   1      id1   2      3</code>
<br><code>:5:  id2   6      id2   7      8</code>
<br><code>:6:  id4   6      id4   7      8</code>
<br><code>:7:  id5   1      id5   2      3</code>
<br><code>:8:  id6   6      id6   7      8</code>
<br><code>:9:  id7   1      id7   2      3</code>
<br><code>:10: id8   6      id8   2      3</code>
<br><code>:11: id9   6      id9   7      8</code>
<br><code>:12: id11  6      id11  7      8</code>
<br><code>:13: id12  6      id12  7      8</code>
<br><code>:14: id14  1      id14  7      8</code>
<br><code>:15: id15  6      id15  2      3</code>
</div>
<br>
<hr class="hr">
</div>
</div>
</body>
