
# New Parameter Scheme

The new (combined) data would be stored as a blob on the `ans_ParameterDocument` item. This could be done in addition to the metadata we have today as a first step.

Sample XML interchange format. Key points:

- Hierarchical data structure to describe the structure of the project (designs, setups, meshes, boundary conditions, key results, etc.)
- A way to associate values with the hierarchical structure. These values could be
  - Scalar primitives (numbers, strings, dates, booleans, ...)
  - File references (images, animations, 3D models, data files)
  - Complex structures:
    - Data tables representing the content of a graph
    - Vectors
    - ....

**Example**: Manually created

```xml
<section name="AC32 Lower Control Arm" role="design">
  <section name="Center of Mass">
    <number name="x" value="642.274" unit="mm" />
    <number name="y" value="-656.016" unit="mm" />
    <number name="z" value="724.847" unit="mm" />
  </section>
  <number name="Mass" value="2.99" unit="kg" />
  <section name="Mass Inertia">
    <number name="XX" value="0.049" unit="kg*m^2" />
    <number name="YY" value="0.045" unit="kg*m^2" />
    <number name="ZZ" value="0.127" unit="kg*m^2" />
    <number name="XY" value="-0.037" unit="kg*m^2" />
    <number name="XZ" value="-0.003" unit="kg*m^2" />
    <number name="YZ" value="0.000" unit="kg*m^2" />
  </section>
</section>
```

**Example**: Automatically extracted from a mechanical file

```xml
<section>
  <file role="subject"
    src="c3-de59094_file_194.rst" 
    created="2019-02-08"
    creator="npathak" 
    appVersion="19.4BETA"
    mimetype="application/ansys-mapdl-rst" />
  <text name="Release Date" value="UP20190206" />
  <text name="Job Name" value="file0" />
  <text name="Units" value="UNDEFINED" />
  <table name="Model Information">
    <columns>
      <input-text readonly="1" name="Entity" />
      <input-number readonly="1" name="Largest_Number" label="Largest Number" step="1" />
      <input-number readonly="1" name="Number_Defined" label="Number Defined" step="1" />
    </columns>
    <row c0="Elements" c1="9" c2="9" />
    <row c0="Nodes" c1="5002" c2="20" />
    <row c0="Element Types" c1="8" c2="4" />
  </table>
  <text name="Active Degrees of Freedom" value="UX UY UZ" />
  <table name="Element Type Information">
    <columns>
      <input-number readonly="1" name="Type" step="1" />
      <input-number readonly="1" name="Number" step="1" />
    </columns>
    <row c0="170" c1="1" />
    <row c0="174" c1="2" />
    <row c0="185" c1="4" />
    <row c0="214" c1="2" />
  </table>
  <section name="Solution Settings">
    <text name="Analysis Type" value="Static (steady-state)" />
  </section>
  <table name="Solution Set Information">
    <columns>
      <input-number readonly="1" name="Set" step="1" />
      <input-number readonly="1" name="tf" label="Time/Frequency" />
      <input-number readonly="1" name="Load_Step" label="Load Step" step="1" />
      <input-number readonly="1" name="Substep" step="1" />
      <input-number readonly="1" name="Cumulative_Iteration" step="1" />
    </columns>
    <row c0="1" c1="51.000" c2="1" c3="1" c4="1" />
    <row c0="2" c1="51.000" c2="1" c3="1" c4="1" />
    <row c0="3" c1="52.000" c2="1" c3="2" c4="2" />
    <row c0="4" c1="52.000" c2="1" c3="2" c4="2" />
    <row c0="5" c1="53.000" c2="1" c3="3" c4="3" />
    <row c0="6" c1="53.000" c2="1" c3="3" c4="3" />
    <row c0="7" c1="54.000" c2="1" c3="4" c4="4" />
    <row c0="8" c1="54.000" c2="1" c3="4" c4="4" />
    <row c0="9" c1="55.000" c2="1" c3="5" c4="5" />
    <row c0="10" c1="55.000" c2="1" c3="5" c4="5" />
    <row c0="11" c1="56.000" c2="1" c3="6" c4="6" />
    <row c0="12" c1="56.000" c2="1" c3="6" c4="6" />
    <row c0="13" c1="57.000" c2="1" c3="7" c4="7" />
    <row c0="14" c1="57.000" c2="1" c3="7" c4="7" />
    <row c0="15" c1="58.000" c2="1" c3="8" c4="8" />
    <row c0="16" c1="58.000" c2="1" c3="8" c4="8" />
    <row c0="17" c1="59.000" c2="1" c3="9" c4="9" />
    <row c0="18" c1="59.000" c2="1" c3="9" c4="9" />
    <row c0="19" c1="60.000" c2="1" c3="10" c4="10" />
    <row c0="20" c1="60.000" c2="1" c3="10" c4="10" />
  </table>
  <table name="Table of Maximum Displacements">
    <columns>
      <input-number readonly="1" name="X" />
      <input-number readonly="1" name="Y" />
      <input-number readonly="1" name="Z" />
      <input-number readonly="1" name="Vector_Sum" label="Vector Sum" />
    </columns>
    <row c0="3.49125E-08" c1="7.45933E-09" c2="-2.30718E-07" c3="2.33121E-07" />
  </table>
  <table name="Table of Minimum and Maximum Stresses">
    <columns>
      <input-text readonly="1" name="min_max" label="Min-Max" />
      <input-number readonly="1" name="p1" label="1st Principal" />
      <input-number readonly="1" name="p3" label="3rd Principal" />
      <input-number readonly="1" name="vm" label="von Mises" />
    </columns>
    <row c0="Minimum" c1="11.456" c2="-80.513" c3="22.759" />
    <row c0="Maximum" c1="80.513" c2="-11.456" c3="123.31" />
  </table>
  <file src="reportFiles/plnsusum.png" role="content" name="Displacement Plot" mimetype="image/png" />
  <file src="reportFiles/plnsseqv.png" role="content" name="Von Mises Stress Plot" mimetype="image/png" />
</section>
```

# Metadata Extraction

The goal of the new format is to be the single file format that stores **ALL** data generated by metadata extraction including:

## File Type Inferencing

```xml
<file role="subject" src="c3-de59094_file_194.rst" mimetype="application/ansys-mapdl-rst" />
```

## Dependency Extraction

```xml
<file role="subject" src="assembly.scdoc">
  <file role="dependency" src="part1.scdoc" />
  <file role="dependency" src="part2.scdoc" />
  <file role="dependency" src="part3.scdoc" />
</file>
```

## Thumbnail

```xml
<file role="subject" src="elbow1.cas.gz" mimetype="application/ansys-fluent-case" appVersion="19.2.0">
  <file role="thumbnail" src="file.png" />
</file>
```

## Viewables

These are not considered separate from the rest of the data (like today), but are embedded in the data much like AEDT

```xml
<section name="Simulation Details Report">
  <file role="subject" src="OptimTee.aedt" appVersion="2019.3" created="2003-05-15T14:43:07Z" mimetype="application/ansys-aedt" />
  <section name="TeeModel" role="design">
    <file src="ekm-report-files/TeeModel/TeeModel.wcax" role="content" name="Design Image" mimetype="model/vcollab-web" />
    <file src="ekm-report-files/TeeModel/TeeModel.png" role="content" name="Design Image" mimetype="image/png" />
  </section>
</section>
```

## Report + Metadata

The rest of the report should represent the combined information of the report and metadata

```xml
<section name="Simulation Details Report">
  <file role="subject" src="elbow1.cas.gz" mimetype="application/ansys-fluent-case" appVersion="19.2.0">
    <file role="thumbnail" src="file.png" />
  </file>
  <file role="content" src="elbow1.wcax" mimetype="model/vcollab-web" />
  <section name="aluminum (solid)" role="material">
    <number name="Density" value="2719" unit="kg/m^3" />
    <number name="Cp (Specific Heat)" value="871" unit="J/(kg K)" />
    <number name="Thermal Conductivity" value="202.4" unit="W/(m K)" />
  </section>
  <section name="fluid">
    <boolean name="Frame Motion?" value="0" />
    <boolean name="Mesh Motion?" value="0" />
  </section>
  <table name="Boundary Zones">
    <columns>
      <input-text readonly="1" name="name" />
      <input-text readonly="1" name="id" />
      <input-text readonly="1" name="type" />
    </columns>
    <row c0="wall" c1="3" c2="wall" />
    <row c0="symmetry" c1="4" c2="symmetry" />
    <row c0="pressure-outlet-7" c1="5" c2="pressure-outlet" />
    <row c0="velocity-inlet-6" c1="6" c2="velocity-inlet" />
    <row c0="velocity-inlet-5" c1="7" c2="velocity-inlet" />
  </table>
</section>
```

## Errors and Logs

User-visible errors and logs generated by the metadata extraction program can be included inline with the report.

```xml
<section name="Simulation Details Report">
  <file role="subject" src="elbow1.cas.gz" mimetype="application/ansys-fluent-case" appVersion="19.2.0">
    <doc role="error" value="Error generating thumbnail: Object reference not set to an instance of an object">
      <text name="StackTrace" value="method() at anotherMethod() at thirdMethod()">
      <text name="Application" value="ExternalApp.exe">
      <date name="ErrorDate" value="2021-05-26T22:00:00Z">
    </doc>
  </file>
</section>
```

# Elements

## Value Elements

- `boolean`: Describes a boolean true/false parameter
  - `name`: Unique identifier for the value.
  - `label`: The human-readable name given to the value. Only include this if it differs from the name.
  - `value`: Use `0` for false or `1` for true
- `date`: Describes a date/time parameter
  - `name`: Unique identifier for the value.
  - `label`: The human-readable name given to the value. Only include this if it differs from the name.
  - `value`: The date (and optionally time). Include a timezone where possible
- `file`: Describes a file parameter
  - `name`: Unique identifier for the value.
  - `label`: The name given to the resource. Only include this if it differs from the name. [Dublin Core: title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/elements/1.1/title)
  - `src`: The relative path of the file
  - `mimetype`: The MIME type of file
  - `role`: The role the file reference plays in the parameter document
    - `subject`: The primary file from which parameters were extracted
    - `content`: An image, model, etc. that is a parameter of the report
    - `thumbnail`: A thumbnail for the subject file
    - `dependency`: A file on which another file depends.
  - `application`: The name of the application that created this file. [Open XML 22.2.2.1: Application Name](https://www.ecma-international.org/wp-content/uploads/ECMA-376-Fifth-Edition-Part-1-Fundamentals-And-Markup-Language-Reference.zip)
  - `appVersion`: The version of the application which produced this file. [Open XML: 22.2.2.2: Application Version](https://www.ecma-international.org/wp-content/uploads/ECMA-376-Fifth-Edition-Part-1-Fundamentals-And-Markup-Language-Reference.zip)
  - `created`: Date of creation of the resource. Should be expressed in UTC. [Dublin Core Terms: created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/created)
  - `creator`: An entity primarily responsible for making the resource. (The user that created the file.) The identification is environment-specific. (Example: A name, email address, or employee ID. end example) It is recommended that this value be as concise as possible. [Dublin Core: creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/elements/1.1/creator)
  - `lastModifiedBy`: The user who performed the last modification. The identification is environment-specific. (Example: A name, email address, or employee ID. end example) It is recommended that this value be as concise as possible. [Open XML 11: Core Properties](http://standards.iso.org/ittf/PubliclyAvailableStandards/c061796_ISO_IEC_29500-2_2012.zip)
  - `modified`: Date on which the resource was changed. Should be expressed in UTC. [Dublin Core Terms: modified](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/modified)
- `number`: Describes a numeric parameter
  - `name`: Unique identifier for the value.
  - `label`: The human-readable name given to the value. Only include this if it differs from the name.
  - `value`: The numeric value
  - `unit`: The unit for the numeric value
- `text`: Describes a string/text parameter
  - `name`: Unique identifier for the value.
  - `label`: The human-readable name given to the value. Only include this if it differs from the name.
  - `value`: The text
- `expression`: An expression which resolves to a value
  - `name`: Unique identifier for the value.
  - `label`: The human-readable name given to the value. Only include this if it differs from the name.
  - `value`: The text of the expression
  - `unit`: The unit the expression evaluates to

## Schema and Placeholders

Schema elements can be used to (1) describe the schema of a table or
(2) represent placeholders ([optiSLang](https://ansysproducthelpdev.win.ansys.com/account/secured?returnurl=/Views/Secured/corp/v212/en/opti_ug/opti_ug_placeholders_proj_overview.html)) or parameters ([Workbench](https://ansysproducthelpdev.win.ansys.com/account/secured?returnurl=/Views/Secured/corp/v212/en/wb2_help/wb2h_parameters.html))

- `input-text`
  - `name`: Unique identifier for the value.
  - `label`: Label for this input.
  - `default_value`: Initial value for this field.
  - `readonly`: Whether or not the user can update this value when running this file
  - `max_length`: Maximum length characters to collect.
  - `pattern`: Regular expression indicating the required format of this text input.
- `input-number`
  - `name`: Unique identifier for the value.
  - `label`: Label for this input.
  - `default_value`: Initial value for this field.
  - `readonly`: Whether or not the user can update this value when running this file
  - `min_range`: Minimum value.
  - `max_range`: Maximum value.
  - `step`: Step size for a numeric input.
  - `unit`
- `input-toggle`
  - `name`: Unique identifier for the value.
  - `label`: Label for this input.
  - `default_value`: Initial value for this field.
  - `readonly`: Whether or not the user can update this value when running this file
- `input-file`
  - `name`: Unique identifier for the value.
  - `label`: Label for this input.
  - `readonly`: Whether or not the user can update this value when running this file
  - `accept`: Defines the file types the file input should accept. This string is a comma-separated list of [unique file type specifiers](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file#unique_file_type_specifiers)
- `input-choice-set`
  - `multi_select`: Allow multiple choices to be selected. ([\<select multiple\>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select#attr-multiple), [Adaptive Cards: isMultiSelect](https://adaptivecards.io/explorer/input-choice-set.html#dedupe-headerismultiselect))
- `input-choice`
  - `label`: Text to display. ([\<option\>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option), [Adaptive Cards: title](https://adaptivecards.io/explorer/input-choice.html#dedupe-headertitle))
  - `value`: The raw value for the choice. ([\<option value\>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option#attr-value), [Adaptive Cards: value](https://adaptivecards.io/explorer/input-choice.html#dedupe-headervalue))

## Grouping Elements

- `section`: A group of parameters
  - `name`: Unique identifier
  - `label`: The human-readable name
  - `role`: The semantic meaning of the group
    - `design`: A particular design
    - `setup`: A simulation setup with specific boundary conditions
    - `boundary`: A particular boundary
    - `material`: Information about a material used
- `doc`: A comment (or log entry) describing sibling elements
  - `value`: Text of the comment
  - `role`:
    - `error`: Details about an error that occurred
    - `warning`: A warning
    - `info`: Information
- `import`: Import parameter information from another parameter file
  - `src`: The relative path of the file

**Example**: Displaying error information from generating the report

Parameters inside the doc comment describe the comment and are ignored as parameters in the overall tree structure

```xml
<doc role="error" value="Error generating thumbnail: Object reference not set to an instance of an object">
  <text name="StackTrace" value="method() at anotherMethod() at thirdMethod()">
  <text name="Application" value="ExternalApp.exe">
  <date name="ErrorDate" value="2021-05-26T22:00:00Z">
</doc>
```

## Table Elements

Tables should be used to describes sets of data (such as parameter tables, charts, etc.). They MUST NOT be used to describe key-value-pair data. That should be done using the [value elements](#value-elements) grouped into [sections](#grouping-elements).

- `table`: A table of data.
  - `name`: Unique identifier
  - `label`: The human-readable name
- `columns`: A list of schemas describing the columns in the table. Up to 30 columns are allowed.
- `row`: An individual row of data
  - `c0` - `c29`: Values of individual columns

**Example**:

```xml
<table name="Parameters">
  <columns>
    <input-text name="Design Point" readonly="0" />
    <input-number name="P1" label="HUB TIP Span Location" readonly="0" />
    <input-number name="P2" label="MESH DATA Edge Count Factor" readonly="0" />
    <input-number name="P5" label="HUB TIP Span Location" readonly="0" unit="m" />
    <input-number name="P3" label="minangle" readonly="1" unit="deg" />
    <input-number name="P4" label="nodes" readonly="1" />
  </columns>
  <row c0="DP0" c1="0.05" c2="1" c3="0.0033237" c4="34.008" c5="158020" />
  <row c0="DP1" c1="0.06" c2="1" c3="0.0033237" c4="32.099" c5="316980" />
  <row c0="DP2" c1="0.052" c2="1" c3="0.0033233" c4="31.156" c5="311480" />
</table>
```

# Examples

To generate this new format from the existing EKM format, you can use the [EKM Report Conversion XSLT](../.attachments/Parameter_LegacyConversion.xslt). That plus the conversion C# code in the appendix were used to generate the following examples:

- [.aedt](../.attachments/aedt_OptimTee_minerva2.xml)
- [.cas (Fluent)](../.attachments/cas.gz_elbow1_minerva2.xml)
- [.catpart (Catia)](../.attachments/CATPart_v5-sample_minerva2.xml)
- [.cdb](../.attachments/cdb_3bodies2mats_minerva2.xml)
- [.db](../.attachments/db_elec_minerva2.xml)
- [.fil](../.attachments/fil_cylinder_minerva2.xml)
- [.iges (CAD)](../.attachments/iges_iges-sample_minerva2.xml)
- [.k (LS Dyna)](../.attachments/k_LS-DYNA-Test-Input_minerva2.xml)
- [.op2](../.attachments/op2_bracket2_minerva2.xml)
- [.opf](../.attachments/opf_base_system_minerva2.xml)
- [.prt (UG)](../.attachments/prt_ug-sample_minerva2.xml)
- [.res](../.attachments/res_StaticMixer_001_minerva2.xml)
- [.rst](../.attachments/rst_case2_minerva2.xml)
- [.sat](../.attachments/sat_cylinder_minerva2.xml)
- [.scdoc (SpaceClaim)](../.attachments/scdoc_MD_minerva2.xml)
- [.stp](../.attachments/stp_export_minerva2.xml)
- [.t16](../.attachments/t16_test2_minerva2.xml)
- [.wbpj (Workbench)](../.attachments/wbpj_Design-Point-Testing-Fluent_minerva2.xml)

These sample should validate with the [XML Schema](../.attachments/ParameterSchema.xsd).

# Appendix: Auto-conversion code

```cs
public async Task DownloadEkmReports()
{
  const string downloadLocation = @"D:\ANSYSDev\Code\SPDM\TechnicalSpecs\examples";
  if (!Directory.Exists(downloadLocation))
  {
    Directory.CreateDirectory(downloadLocation);
  }
  else
  {
    foreach (var file in Directory.GetFiles(downloadLocation))
      File.Delete(file);
  }

  var conn = new HttpConnection("https://cdcw16spdmqa01.win.ansys.com/ANSYSMinerva/");
  await conn.LoginAsync(new ExplicitCredentials("MinervaQA", "admin", "minerva"));
  var names = (await conn.ExecuteAsync(Query.Aml(@"<Item action='get' type='Ans_Data' select='report_xml,name,local_file(filename,file_type(mimetype)),thumbnail,author,date_content_created,date_content_modified,application_version,viewable_file,view_file' orderBy='created_on DESC' maxRecords='500'>
  <report_xml condition='is not null'></report_xml>
  <Relationships>
    <Item action='get' type='ans_DataParameter' select='path,name,value' />
    <Item action='get' type='ans_DataDependsOn' select='path,related_id' />
  </Relationships>
</Item>"))).Items()
    .GroupBy(i => (string)i.Properties["report_xml"])
    .Select(g => g.First())
    .GroupBy(i => (string)i.Properties["name"], StringComparer.OrdinalIgnoreCase)
    .ToDictionary(g => (string)g.First().Properties["report_xml"]
      , g => g.First());
  var files = await conn.ExecuteAsync(Query.GetFiles(names.Keys));
  var nameXref = new Dictionary<string, Item>();
  foreach (var file in files)
  {
    var parts = ((string)names[file.Id].Properties["name"]).Split('.');
    var extensionCount = 1;
    if (parts.Length > 2 && parts.Last() == "gz" || int.TryParse(parts.Last(), out var _))
      extensionCount = 2;
    var newName = string.Join('.', parts, parts.Length - extensionCount, extensionCount)
      + "_" + string.Join('.', parts, 0, parts.Length - extensionCount);
    file.RelativePath = newName + "_ekm.xml";
    nameXref[file.RelativePath] = names[file.Id];

    using (var writer = XmlWriter.Create(Path.Combine(downloadLocation, newName + "_aml.xml"), new XmlWriterSettings()
    {
      OmitXmlDeclaration = true,
      Indent = true,
      IndentChars = "  "
    }))
    {
      names[file.Id].ToXml(writer, conn.Session);
    }
  }
  var vault = await conn.VaultAsync();
  await vault.DownloadAsync(files, downloadLocation);

  var thumbnails = nameXref.Values
    .Where(i => i.Properties.HasValue("thumbnail"))
    .Select(i => ((string)i.Properties["thumbnail"]).Substring(17))
    .Distinct()
    .ToList();
  var thumbnailNames = (await conn.ExecuteAsync(Query.Aml($"<Item type='File' action='get' select='filename' idlist='{string.Join(",", thumbnails)}' />")))
    .Items()
    .ToDictionary(i => i.Id, i => (string)i.Properties["filename"]);
  foreach (var item in nameXref.Values)
  {
    if (item.Properties.HasValue("thumbnail") 
      && thumbnailNames.TryGetValue(((string)item.Properties["thumbnail"]).Substring(17), out var name))
    {
      item.Properties["thumbnail"].Attributes.Set("name", name);
    }
  }

  var convTaskXRef = (await conn.ExecuteAsync(Query.Aml($@"<Item type='ConversionTask' action='get' select='md_error_info,file_id'>
  <file_id condition='in'>'{string.Join("','", nameXref.Values
    .Where(i => i.Properties.HasValue("local_file"))
    .Select(i => (string)i.Properties["local_file"])
    .Distinct())}'</file_id>
  <and>
    <md_error_info condition='is not null' />
    <md_error_info condition='ne'>&lt;errors /&gt;</md_error_info>
  </and>
</Item>")))
    .Items()
    .ToDictionary(i => (string)i.Properties["file_id"], i => XElement.Parse((string)i.Properties["md_error_info"]));

  // Load the style sheet.
  var xslt = new XslCompiledTransform();
  xslt.Load(@"D:\ANSYSDev\Code\SPDM\TechnicalSpecs\minerva-spec\.attachments\Parameter_LegacyConversion.xslt");

  var schemaSettings = new XmlReaderSettings();
  schemaSettings.Schemas.Add(null, @"D:\ANSYSDev\Code\SPDM\TechnicalSpecs\minerva-spec\.attachments\ParameterSchema.xsd");
  schemaSettings.ValidationType = ValidationType.Schema;
  var validationBuilder = new StringBuilder();
  schemaSettings.ValidationEventHandler += (s, e) =>
  {
    var reader = (XmlReader)s;
    validationBuilder.Append(Path.GetFileName(reader.BaseURI));
    if (reader is IXmlLineInfo lineInfo && lineInfo.HasLineInfo())
    {
      validationBuilder.Append('[');
      validationBuilder.Append(lineInfo.LineNumber);
      validationBuilder.Append(',');
      validationBuilder.Append(lineInfo.LinePosition);
      validationBuilder.Append(']');
    }
    validationBuilder.Append(": ");
    validationBuilder.Append(e.Severity).Append(": ").Append(e.Message).AppendLine();
  };

  foreach (var file in Directory.GetFiles(downloadLocation, "*_ekm.xml"))
  {
    var newName = Path.GetFileName(file);
    newName = newName.Substring(0, newName.Length - 8);
    var newPath = Path.Combine(downloadLocation, newName + "_minerva.xml");

    var doc = new XDocument();
    using (var reader = XmlReader.Create(file, new XmlReaderSettings()
    {
      IgnoreWhitespace = true
    }))
    using (var writer = doc.CreateWriter())
      xslt.Transform(reader, writer);
    ImproveTransform(doc);
    doc.Save(newPath);

    var item = nameXref[Path.GetFileName(file)];
    if (!convTaskXRef.TryGetValue((string)item.Properties["local_file"], out var convTaskError))
      convTaskError = null;
    AddExternalInfo(doc, item, convTaskError);
    var v2Path = Path.Combine(downloadLocation, newName + "_minerva2.xml");
    doc.Save(v2Path);

    validationBuilder.Clear();
    using (var reader = XmlReader.Create(v2Path, schemaSettings))
    {
      while (reader.Read()) { }
    }
    if (validationBuilder.Length > 0)
    {
      File.WriteAllText(Path.Combine(downloadLocation, newName + "_errors.log"), validationBuilder.ToString());
      validationBuilder.Clear();
    }
  }
}

private void ImproveTransform(XDocument doc)
{
  var subject = doc.Descendants("file").First(e => (string)e.Attribute("role") == "subject");
  var properties = doc.Descendants("section")
    .FirstOrDefault(e => ResolveName((string)e.Attribute("name")) == ResolvedName.Properties);
  if (properties != null)
  {
    foreach (var element in properties.Elements()
      .Where(e => !string.IsNullOrEmpty((string)e.Attribute("name")))
      .ToList())
    {
      var resolved = ResolveName((string)element.Attribute("name"));
      if (resolved == ResolvedName.Unknown)
      {
        // Do nothing
      }
      else if (resolved == ResolvedName.Remove)
      {
        element.Remove();
      }
      else
      {
        if (subject.Attribute(resolved.ToString()) == null
          && !string.IsNullOrEmpty((string)element.Attribute("value")))
        {
          switch (resolved)
          {
            case ResolvedName.created:
            case ResolvedName.modified:
              var dateString = (string)element.Attribute("value");
              if (resolved == ResolvedName.created)
              {
                var timeString = (string)properties
                  .Elements()
                  .FirstOrDefault(e => (string)e.Attribute("name") == "Creation Time"
                    || (string)e.Attribute("name") == "Time:")
                  ?.Attribute("value");
                if (!string.IsNullOrEmpty(timeString))
                  dateString += " " + timeString;
              }
              if (TryParseDate(dateString, out var parsed))
                subject.SetAttributeValue(resolved.ToString(), parsed.ToUniversalTime().ToString("s") + "Z");
              break;
            default:
              var value = (string)element.Attribute("value");
              if (!string.Equals(value, "Unknown", StringComparison.OrdinalIgnoreCase))
                subject.SetAttributeValue(resolved.ToString(), value);
              break;
          }
        }

        element.Remove();
      }
    }

    if (!properties.Elements().Any())
      properties.Remove();
  }
}

private void AddExternalInfo(XDocument doc, Item item, XElement conversionTaskError)
{
  var localFile = item.Properties["local_file"].AsItem();
  var fileType = localFile.Properties["file_type"].AsItem();
  var subject = doc.Descendants("file").First(e => (string)e.Attribute("role") == "subject");
  subject.SetAttributeValue("src", (string)localFile.Properties["filename"]);
  if (fileType?.Properties.HasValue("mimetype") == true)
    subject.SetAttributeValue("mimetype", (string)fileType.Properties["mimetype"]);

  if (item.Properties.HasValue("application_version"))
    subject.SetAttributeValue("appVersion", (string)item.Properties["application_version"]);
  if (item.Properties.HasValue("author"))
    subject.SetAttributeValue("creator", (string)item.Properties["author"]);
  if (item.Properties.HasValue("date_content_created"))
    subject.SetAttributeValue("created", ((DateTime)item.Properties["date_content_created"]).ToUniversalTime().ToString("s") + "Z");
  if (item.Properties.HasValue("date_content_modified"))
    subject.SetAttributeValue("modified", ((DateTime)item.Properties["date_content_modified"]).ToUniversalTime().ToString("s") + "Z");

  if (item.Properties["thumbnail"]?.Attributes.HasValue("name") == true)
  {
    subject.Add(new XElement("file"
      , new XAttribute("role", "thumbnail")
      , new XAttribute("src", item.Properties["thumbnail"].Attributes["name"])));
    if (item.Relationships.Any(i => string.Equals(i.Type, "ans_DataDependsOn", StringComparison.OrdinalIgnoreCase))
      && !subject.Elements("file").Any(e => (string)e.Attribute("role") == "dependency"))
    {
      foreach (var path in item.Relationships.Where(i => string.Equals(i.Type, "ans_DataDependsOn", StringComparison.OrdinalIgnoreCase))
        .Select(i => (string)i.Properties["path"])
        .Distinct())
      {
        subject.Add(new XElement("file"
          , new XAttribute("role", "dependency")
          , new XAttribute("src", path)));
      }
    }
  }

  var viewable = (string)item.Properties["viewable_file"]?.Attributes["keyed_name"]
    ?? (string)item.Properties["view_file"]?.Attributes["keyed_name"];
  if (!string.IsNullOrEmpty(viewable) && viewable != (string)localFile.Properties["filename"])
  {
    var mimetype = "model/*";
    switch (Path.GetExtension(viewable).ToUpperInvariant())
    {
      case ".AVZ":
        mimetype = "model/ansys-viewer";
        break;
      case ".WCAX":
        mimetype = "model/vcollab-web";
        break;
      case ".SCS":
        mimetype = "model/hoops-scs";
        break;
    }
    subject.AddAfterSelf(new XElement("file"
      , new XAttribute("role", "content")
      , new XAttribute("src", viewable)
      , new XAttribute("mimetype", mimetype)));
  }

  foreach (var error in (conversionTaskError?.Elements("error") ?? Enumerable.Empty<XElement>()))
  {
    var docElem = new XElement("doc");
    docElem.SetAttributeValue("role", "error");
    docElem.SetAttributeValue("value", (string)error.Element("message"));
    foreach (var element in error.Elements().Where(e => !string.IsNullOrEmpty((string)e)))
    {
      docElem.Add(new XElement("text", new XAttribute("name", element.Name.LocalName), new XAttribute("value", (string)element)));
    }
    subject.AddAfterSelf(docElem);
  }
}

private bool TryParseDate(string value, out DateTime date)
{
  if (DateTime.TryParse(value, out date))
    return true;
  if (DateTime.TryParseExact(value, "ddd MMM d HH:mm:ss yyyy", System.Globalization.CultureInfo.InvariantCulture, System.Globalization.DateTimeStyles.None, out date))
    return true;
  return false;
}

private enum ResolvedName
{
  Unknown,
  Properties,
  created,
  application,
  appVersion,
  creator,
  src,
  label,
  modified,
  Remove
}

private ResolvedName ResolveName(string name)
{
  switch (name)
  {
    case "Project Properties": // AEDT
    case "Model Information": // VCollab CAD
    case "File Parameters": // LS Dyna
    case "File Information": // Mechanical
    case "General Info": // optiSLang
    case "Summary": // Workbench
      return ResolvedName.Properties;
    case "Date Created":
    case "Creation Date":
    case "Header  DATE":
    case "Date:":
      return ResolvedName.created;
    case "CAD Package Version":
    case "Version":
    case "Release":
    case "optiSLang rev.":
    case "Product Version:":
      return ResolvedName.appVersion;
    case "CAD Package Name":
    case "Solver":
      return ResolvedName.application;
    case "Author":
    case "Author Name":
      return ResolvedName.creator;
    case "Model File":
      return ResolvedName.src;
    case "Title":
    case "project name":
    case "Project:":
      return ResolvedName.label;
    // We don't need the file size
    case "File Size":
    case "Creation Time":
    case "Time:":
      return ResolvedName.Remove;
    case "last saved":
      return ResolvedName.modified;
    default:
      return ResolvedName.Unknown;
  }
}
```

# Appendix: Current Data Model (2021 R2)

```plantuml
class ans_Data {
  local_file : item[File]
  report_xml : item[File]
}

class ans_DataParameter {
  path : string
  name : string
  value : string
}
ans_Data --> ans_DataParameter : source_id

class ans_DataFile {
  path : string
  related_id : item[File]
}
ans_Data --> ans_DataFile : source_id
```

The report XML file looks something like

```xml
<section>
    <table name="General Info">
        <column name="Condition"/>
        <column name="Value"/>
        <row>
            <value>project name</value>
            <value>Custom Project</value>
        </row>
        <row>
            <value>version</value>
            <value>1.0</value>
        </row>
    </table>
    <image name="test preview" src="reportFiles/file.png"/>
</section>
```

The metadata that ends up in the `ans_DataParameter` relationship starts out looking like

```xml
<meta-data>
    <data name="projectName" value="Custom Project"/>
    <data name="version" value="1.0"/>
    <data name="architecture" value="Win64"/>
    <data name="lastSaveTime" value=""/>
    <data name="Created By" value=""/>
    <child name="Design1" type="Design">
        <data name="Type" value="Modal"/>
        <data name="Boundaries" value="region1,region2"/>
        <data name="Formulation" value="Explicit"/>
    </child>
</meta-data>
```

# Appendix: Current Properties

- CFX
  - version : `string`
  - time : `string`
  - domains : `array[object]`
    - name : `string`
    - boundaries : `array[object]`
      - name : `string`
  - models : `array[object]`
    - type : `enum[Combustion Model|Heat Transfer Model|Thermal Radiation Model|Turbulence Model]`
    - options : `array[string]`
  - materials : `array[object]`
    - name : `string`
- Fluent
  - version : `string`
  - models : Should we actually represent these as models like the UI does?
    - space : `enum[2d|3d|axisymmetric|axisymmetric-swirl]`
    - time : `enum[steady|unsteady]`
    - solver : `enum[coupled|segregated]`
    - formulation : `enum[explicit|implicit]`
    - viscous : `enum[inviscid|laminar|k-epsilon|k-omega|reynold-stress|v2f|spalart-allmaras|detachedEddy|largeEddy|mixingLength]`
    - radiation : `enum[rosseland|p1|surfaceToSurface|discreteTransfer|discreteOrdinate]`
    - multiphase : `enum[volumeOfFluid|eulerian|mixture|off]`
    - heat transfer : `boolean`
    - dispersed phase : `boolean`
  - materials : `array[object]`
    - name
    - type
    - … other properties ??
  - threads
    - name : thread name is also referred to as a "region"
    - type
    - id
- Fluent Mesh -> VCollab
- HFSS -> ?
- MAPDL
  - analysis types : `array[string]`
  - element types : `array[string]`
  - version : `string`
- Ansys Db
  - version : `string`
  - creation date : `datetime`
  - analysis type : `enum[Static|Modal|Harmonic|Transient|Spectrum|Eigen Buckling|Substructuring]`
  - load steps : `integer`
  - sub steps : `integer`
  - iterations : `integer`
  - components : `array[string]`
  - number of elements : `integer`
  - element types : `array[string]`
  - boundary condition types : `array[string]`
  - contact types : `array[enum[Standard|Rough|No separation (sliding permitted)|Bonded|No separation (always)|Bonded (always)|Bonded (initial contact)]]`
  - dimensionality : `array[enum[2D|Axisymmetric|Axisymmetric harmonic|3D|Generalized axisymmetric]]`
  - large deformation : `boolean`
  - material models : `array[string]`
- Mechanical -> ?
- OptisLang
  - last save time : `dateTime`
  - version : `string`
  - architecture : `string`
  - placeholders : `array[string]`
  - annotations : `array[string]`
- SpaceClaim
  - category : `string`
  - content status : `string`
  - date created : `datetime`
  - creator : `string`
  - description : `string`
  - identifier : `string`
  - keywords : `string`
  - language : `string`
  - date modified : `datetime`
  - revision : `string`
  - subject : `string`
  - title : `string`
  - version : `string`
  - dependencies : `array[string]`
  - is assembly : `boolean`
- VCollab -> ?
- Workbench
