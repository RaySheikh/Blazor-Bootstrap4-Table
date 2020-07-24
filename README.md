## Blazor BootStrap4 Responsive Tables

![hippo](https://doc-10-3g-docs.googleusercontent.com/docs/securesc/arjs1d2a52pemrlg2863g4g7v9mqg5l6/gpalmi4sc93a4ig9md6qe50n6se8e9vc/1595550825000/15266141592163550069/15266141592163550069/1TOq53cXz_mC1DIjmOs-rmKw3iVBoldii?e=view&authuser=0&nonce=tkg379lm4so62&user=15266141592163550069&hash=11ruvgame3mfaja8n3d749e18fd5039p)

Works with Blazor Serverside project.

[Install using nuget package manager:](https://www.nuget.org/packages/BlazorBootstrap4Table/)
```
Install-Package BlazorBootstra4Table -Version 1.1.0
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
Please reference latest boostrap 4 stylesheet in _Host.cshtml head tag.

### Future Enhancements:
- Responsive: Done!
- Pagination
- Sorting
- Search

