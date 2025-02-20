---
layout: post
title: Overview of Syncfusion license registration - Syncfusion
description: Learn here about how to register Syncfusion blazor license key for syncfusion Blazor application with license validation. 
platform: Blazor
component: Common
documentation: ug
---

# Register Syncfusion License Key in a Razor Class Library Application

The generated license key is just a string that might be registered before any Syncfusion control is initiated. The following code is used to register the license.

{% tabs %}
{% highlight c# %}

Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");

{% endhighlight %}
{% endtabs %}

N> * Place the license key between double quotes.  Also, ensure that Syncfusion.Licensing.dll is referenced in your project where the license key is being registered.
* Syncfusion license validation is done offline during application execution and does not require internet access.  Apps registered with a Syncfusion license key can be deployed on any system that does not have an internet connection.

If your Razor Class Library (RCL) project uses Syncfusion Blazor packages from [nuget.org](https://www.nuget.org/packages?q=syncfusion) or the trial installer, you must register your license key. We need to register the license key in RCL project similar to how we do for the Blazor project based on your application type (Server application / Client WebAssembly application).

Refer to this [link](https://blazor.syncfusion.com/documentation/getting-started/razor-class-library/) for more information on getting started with the Syncfusion Blazor components in the RCL project.

## Blazor Server App

After configuring the RCL project with your Blazor Server application, register the license key in Configure method of Startup.cs

Refer to this [link](https://blazor.syncfusion.com/documentation/getting-started/razor-class-library/#getting-started-with-razor-class-library-in-blazor-server-application) for more information on getting started with RCL in the Blazor Server application.

* For .NET 6 and .NET 7 app, open the **~/Program.cs** file and register the Syncfusion license key.

* For .NET 5 and .NET 3.X app, open the **~/Startup.cs** file and register the Syncfusion license key.

{% tabs %}

{% highlight C# tabtitle=".NET 6 & .NET 7 (~/Program.cs)" hl_lines="2 3" %}

var app = builder.Build();
//Register Syncfusion license
Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
    app.UseHsts();
}

{% endhighlight %}

{% highlight c# tabtitle=".NET 3.X & .NET 5 (~/Startup.cs)" hl_lines="4 5" %}

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // Register Syncfusion license
    Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");

    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapBlazorHub();
        endpoints.MapFallbackToPage("/_Host");
    });
}

{% endhighlight %}

{% endtabs %}

## Blazor WebAssembly App

After configuring the RCL project with your Blazor Client WebAssembly application, register the license key in main method of Program.cs

Refer to this [link](https://blazor.syncfusion.com/documentation/getting-started/razor-class-library/#getting-started-with-razor-class-library-in-blazor-clientwebassembly-application) for more information on getting started with RCL in the Blazor Client WebAssembly application.

{% tabs %}

{% highlight c# tabtitle="~/Program.cs" hl_lines="3 4" %}

public static async Task Main(string[] args)
{
    // Register Syncfusion license
    Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");

    ....
    ....
}

{% endhighlight %}

{% endtabs %}