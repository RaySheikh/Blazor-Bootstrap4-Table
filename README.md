## Blazor BootStrap4 Responsive Tables

![example](https://drive.google.com/uc?export=view&id=1nyvokb4fPSA-qe_NJ7Au1P28vakXLM4s)

Works with Blazor Serverside or WebAssembly.

[Install using nuget package manager:](https://www.nuget.org/packages/BlazorBootstrap4Table/)
```
Install-Package BlazorBootstra4Table -Version 1.2.1
```
Usage:
```
@page "/fetchdata"
@inject HttpClient Http
@using BlazorBootstrap4Table

<h1>Weather forecast</h1>

<p>Blazor Bootstrap 4 Rresponsive Table</p>

    <Table Items="@forecasts" Striped="table-striped">
        <TableHeader>

            <th>Date</th>
            <th>Temp. (C)</th>
            <th>Temp. (F)</th>
            <th>Summary</th>

        </TableHeader>
        <TableRow>
            <td mobile-header="Date">@context.Date.ToShortDateString()</td>
            <td mobile-header="Temp. (C)">@context.TemperatureC</td>
            <td mobile-header="Temp. (F)">@context.TemperatureF</td>
            <td mobile-header="Summary">@context.Summary</td>
        </TableRow>
    </Table>
}

@code {
    private List<WeatherForecast> forecasts;

    protected override async Task OnInitializedAsync()
    {
        forecasts = await Http.GetFromJsonAsync<List<WeatherForecast>>("sample-data/weather.json");
    }

    public class WeatherForecast
    {
        public DateTime Date { get; set; }

        public int TemperatureC { get; set; }

        public string Summary { get; set; }

        public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
    }
}
```
Enable Search Filter: 
GetFilterableText = Fun<TItem, String>
Pass items you want searchbar to filter
```
<Table Items="@forecasts" Striped="table-striped" GetFilterableText=@(item => $"{item.Date} {item.Summary} {item.TemperatureC} {item.TemperatureF}" )>
```
Link CSS file:
```
//Add to index.html file in wwwroot folder
<link href="_content/BlazorBootstrap4Table/styles.css" rel="stylesheet"/>
```
Please reference latest boostrap 4 stylesheet in _Host.cshtml head tag.

### Future Enhancements:
- ~~Responsive~~: Done!
- ~~Search~~: Done!
- Pagination
- Sorting


