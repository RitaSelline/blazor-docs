---
layout: post
title: Sorting in Blazor Pivot Table Component | Syncfusion
description: Checkout and learn here all about sorting in Syncfusion Blazor Pivot Table component and much more details.
platform: Blazor
control: Pivot Table
documentation: ug
---

<!-- markdownlint-disable MD012 -->

# Sorting in Blazor Pivot Table Component

## Member Sorting

Allows to order field members in rows and columns either in ascending or descending order. By default, field members in rows and columns are in ascending order.

Member sorting can be enabled by setting the [EnableSorting](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.DataSourceSettingsModel-1.html#Syncfusion_Blazor_PivotView_DataSourceSettingsModel_1_EnableSorting) property in [PivotViewDataSourceSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewDataSourceSettings-1.html) class to **true**. After enabling this API, click the sort icon besides each field in row or column axis, available in the field list or grouping bar UI for re-arranging members either in ascending or descending order.

> By default the [EnableSorting](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.DataSourceSettingsModel-1.html#Syncfusion_Blazor_PivotView_DataSourceSettingsModel_1_EnableSorting) property in [PivotViewDataSourceSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewDataSourceSettings-1.html) class set as **true**. If it is set as **false**, then the field members arrange in pivot table as its data source order. And, the sort icons in grouping bar and field list buttons will be removed.

![Sorting in Blazor PivotTable Field List](images/blazor-pivottable-sorting-in-field-list.png)
<br/>
![Sorting in Blazor PivotTable Grouping Bar](images/blazor-pivottable-sorting-in-groupbar.png)
<br/>
![Sorting in Blazor PivotGrid](images/blazor-pivotgrid-sorting.png)

Member sorting can also be configured using the [PivotViewSortSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html) class through the code behind, during the initial rendering. The settings required to sort are:

* [Name](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html#Syncfusion_Blazor_PivotView_PivotViewSortSetting_Name): It allows to set the field name.
* [Order](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html#Syncfusion_Blazor_PivotView_PivotViewSortSetting_Order): It allows to set the sort direction either to ascending or descending of the respective field.

> By default the [Order](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html#Syncfusion_Blazor_PivotView_PivotViewSortSetting_Order) property in the [PivotViewSortSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html) class set as [Sorting.Ascending](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.Sorting.html). Meanwhile, the field members can arrange its order in data source by setting it as [Sorting.None](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.Sorting.html) where the sort icons in grouping bar and field list buttons for the corresponding field will be removed.

```cshtml
@using Syncfusion.Blazor.PivotView

<SfPivotView TValue="ProductDetails" ShowGroupingBar="true">
     <PivotViewDataSourceSettings DataSource="@data" EnableSorting=true>
        <PivotViewColumns>
            <PivotViewColumn Name="Year"></PivotViewColumn>
            <PivotViewColumn Name="Quarter"></PivotViewColumn>
        </PivotViewColumns>
        <PivotViewRows>
            <PivotViewRow Name="Country"></PivotViewRow>
            <PivotViewRow Name="Products"></PivotViewRow>
        </PivotViewRows>
        <PivotViewValues>
            <PivotViewValue Name="Sold" Caption="Unit Sold"></PivotViewValue>
            <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
        </PivotViewValues>
        <PivotViewFormatSettings>
            <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
        </PivotViewFormatSettings>
        <PivotViewSortSettings>
            <PivotViewSortSetting Name="Country" Order=Sorting.Descending></PivotViewSortSetting>
        </PivotViewSortSettings>
    </PivotViewDataSourceSettings>
</SfPivotView>

@code{
    public List<ProductDetails> data { get; set; }
    protected override void OnInitialized()
    {
        this.data = ProductDetails.GetProductData().ToList();
        //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
    }
}

```

![Sorting in Blazor PivotGrid](images/blazor-pivotgrid-sorting.png)

### Alphanumeric Sorting

Usually string sorting is applied to field members even if it starts with numbers. But this kind of field members can also be sorted on the basis of the numbers that are placed at the beginning of the member name. This can be achieved by setting the [DataType](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.FieldOptionsModel.html#Syncfusion_Blazor_PivotView_FieldOptionsModel_DataType) property as number to the desired field.

```cshtml
@using Syncfusion.Blazor.PivotView

<SfPivotView ID="PivotView" TValue="AlphaNumericData" Width="100%" Height="600" ShowGroupingBar="true" ShowFieldList="true" ShowTooltip="false">
    <PivotViewDataSourceSettings DataSource="@pivotData" ExpandAll="false" AllowMemberFilter="true" EnableSorting=true>
        <PivotViewColumns>
            <PivotViewColumn Name="Units"></PivotViewColumn>
        </PivotViewColumns>
        <PivotViewRows>
            <PivotViewRow Name="Product"></PivotViewRow>
        </PivotViewRows>
        <PivotViewValues>
            <PivotViewValue Name="Sold" Caption="Units Sold"></PivotViewValue>
            <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
        </PivotViewValues>
        <PivotViewFieldMapping>
            <PivotViewField Name="Units" DataType="number"></PivotViewField>
        </PivotViewFieldMapping>
    </PivotViewDataSourceSettings>
</SfPivotView>

@code{
    public List<AlphaNumericData> data { get; set; }
    protected override void OnInitialized()
    {
        this.data = AlphaNumericData.GetProductData().ToList();
        //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
    }
}

```

![Alpha Numeric Sorting in Blazor PivotTable](images/blazor-pivottable-alpha-numberic-sorting.png)

### Custom Sorting

Allows to sort field headers (aka, members) in rows and columns based on user-defined order. This can be configured mainly using the [membersOrder]() in the [PivotViewSortSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html) class through code behind, during initial rendering. The other settings required to sort are:

* [Name](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html#Syncfusion_Blazor_PivotView_PivotViewSortSetting_Name): It allows to set the field name.
* [MembersOrder](): It holds an array of headers in the order specified by the user.
* [Order](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewSortSetting.html#Syncfusion_Blazor_PivotView_PivotViewSortSetting_Order): It allows to specify whether the array of headers should be sorted ascending or descending.

```cshtml
@using Syncfusion.Blazor.PivotView

<SfPivotView TValue="ProductDetails" Height="350" ShowGroupingBar="true">
     <PivotViewDataSourceSettings DataSource="@data" ExpandAll="false" EnableSorting=true>
        <PivotViewColumns>
            <PivotViewColumn Name="Year"></PivotViewColumn>
            <PivotViewColumn Name="Quarter"></PivotViewColumn>
        </PivotViewColumns>
        <PivotViewRows>
            <PivotViewRow Name="Country"></PivotViewRow>
            <PivotViewRow Name="Products"></PivotViewRow>
        </PivotViewRows>
        <PivotViewValues>
            <PivotViewValue Name="Sold" Caption="Unit Sold"></PivotViewValue>
            <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
        </PivotViewValues>
        <PivotViewSortSettings>
            <PivotViewSortSetting Name="Country" Order=Sorting.Ascending MembersOrder="@(new string[] {"United States","France"})"></PivotViewSortSetting>
            <PivotViewSortSetting Name="Year" Order=Sorting.Descending MembersOrder="@(new string[] {"FY 2015","FY 2017"})"></PivotViewSortSetting>
        </PivotViewSortSettings>
    </PivotViewDataSourceSettings>
</SfPivotView>

@code{
    public List<ProductDetails> data { get; set; }
    protected override void OnInitialized()
    {
        this.data = ProductDetails.GetProductData().ToList();
        //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
    }
}

```

![Custom Sorting in Blazor PivotTable](images/blazor-pivottable-custom-sorting.png)

## Value sorting

> This property is applicable only for relational data source.

Allows to sort individual value field and its aggregated values either in row or column axis in both ascending and descending order. It can be enabled by setting the [EnableValueSorting](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.SfPivotView-1.html#Syncfusion_Blazor_PivotView_SfPivotView_1_EnableValueSorting) property in [SfPivotView](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.SfPivotView-1.html) class to **true**. On enabling, the end user can sort the values by directly clicking the value field header positioned either in row or column axis of the pivot table component.

The value sorting can also be configured using the [PivotViewValueSortSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewValueSortSettings.html) option through the code behind. The settings required to sort value fields are:

* [HeaderText](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewValueSortSettings.html#Syncfusion_Blazor_PivotView_PivotViewValueSortSettings_HeaderText): It allows to set the header names with delimiters, that is used for value sorting. The header names are arranged from Level 1 to Level N, down the hierarchy with a delimiter for better specification.
* [HeaderDelimiter](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewValueSortSettings.html#Syncfusion_Blazor_PivotView_PivotViewValueSortSettings_HeaderDelimiter): It allows to set the delimiters string to separate the header text between levels.
* [SortOrder](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.PivotView.PivotViewValueSortSettings.html#Syncfusion_Blazor_PivotView_PivotViewValueSortSettings_SortOrder): It allows to set the sort direction of the value field.

> Value fields are set to the column axis by default. In such cases, the value sorting applied will have an effect on the column alone. You need to place the value fields in the row axis to do so in row wise. For more information, please [refer here](https://blazor.syncfusion.com/documentation/pivot-table/data-binding/#values-in-row-axis).

```cshtml
@using Syncfusion.Blazor.PivotView

<SfPivotView TValue="ProductDetails" EnableValueSorting="true">
     <PivotViewDataSourceSettings DataSource="@data">
        <PivotViewColumns>
            <PivotViewColumn Name="Year"></PivotViewColumn>
            <PivotViewColumn Name="Quarter"></PivotViewColumn>
        </PivotViewColumns>
        <PivotViewRows>
            <PivotViewRow Name="Country"></PivotViewRow>
            <PivotViewRow Name="Products"></PivotViewRow>
        </PivotViewRows>
        <PivotViewValues>
            <PivotViewValue Name="Sold" Caption="Unit Sold"></PivotViewValue>
            <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
        </PivotViewValues>
        <PivotViewFormatSettings>
            <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
        </PivotViewFormatSettings>
        <PivotViewValueSortSettings HeaderText="FY 2015##Sold Amount" HeaderDelimiter="##" SortOrder=Sorting.Descending></PivotViewValueSortSettings>
    </PivotViewDataSourceSettings>
</SfPivotView>

@code{
    public List<ProductDetails> data { get; set; }
    protected override void OnInitialized()
    {
        this.data = ProductDetails.GetProductData().ToList();
        //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
    }
}

```

![Value Sorting in Blazor PivotTable](images/blazor-pivottable-value-sorting.png)

## Event

### OnHeadersSort

When sorting is applied, the event [OnHeadersSort]() triggers every time while rendering each row and column header cell. This allows the user to re-arrange the order in which the pivot table's headers appear. It has the following parameters:

* `FieldName`: It holds the field name where the sort settings applied.
* `SortOrder`: It holds the current sort order of the field.
* `Members`: It holds the sorted headers according to the specified sort order.
* `LevelName`: It holds the specific field's unique level name. **Note:** This option is applicable only for OLAP data.
* `IsOrderChanged`: By setting this boolean property to true, it allows to display the modified members order.

```cshtml
@using Syncfusion.Blazor.PivotView

<SfPivotView TValue="ProductDetails" Height="350" ShowGroupingBar="true">
     <PivotViewDataSourceSettings DataSource="@data" ExpandAll="false" EnableSorting=true>
        <PivotViewColumns>
            <PivotViewColumn Name="Year"></PivotViewColumn>
            <PivotViewColumn Name="Quarter"></PivotViewColumn>
        </PivotViewColumns>
        <PivotViewRows>
            <PivotViewRow Name="Country"></PivotViewRow>
            <PivotViewRow Name="Products"></PivotViewRow>
        </PivotViewRows>
        <PivotViewValues>
            <PivotViewValue Name="Sold" Caption="Unit Sold"></PivotViewValue>
            <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
        </PivotViewValues>
    </PivotViewDataSourceSettings>
    <PivotViewEvents TValue="ProductDetails" OnHeadersSort="onHeadersSort" ></PivotViewEvents>
    <PivotViewGridSettings ColumnWidth="140"></PivotViewGridSettings>
</SfPivotView>

@code{
    public List<ProductDetails> data { get; set; }
    protected override void OnInitialized()
    {
        this.data = ProductDetails.GetProductData().ToList();
        //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
    }
    private void onHeadersSort(HeadersSortEventArgs args)
    {
        if(args.FieldName == "Country")
        {
            args.Members = new string[] { "United States","Germany"};
            args.IsOrderChanged = true;
        }
        if(args.FieldName == "Year")
        {
            args.Members = new string[] { "FY 2017","FY 2015"};
            args.IsOrderChanged = true;
        }
    }
}

```

> You can refer to the [Blazor Pivot Table](https://www.syncfusion.com/blazor-components/blazor-pivot-table) feature tour page for its groundbreaking feature representations. You can also explore the [Blazor Pivot Table example](https://blazor.syncfusion.com/demos/pivot-table/default-functionalities?theme=bootstrap4) to know how to render and configure the pivot table.