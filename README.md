# Farst DateTime Converter

![Hex.pm](https://img.shields.io/hexpm/l/grpc) ![Nuget](https://img.shields.io/nuget/v/FarStudio.Utility.Parser)
### AUTHOR : FARID PERMANA 

## Formating for property of DTO (data transfer object) Class.

Requirement : 
 -  Newtonsoft.Json 12.0.0

## How to use :
 1. Open **package manager
 2. Type : Install-Package FarStudio.Utility.Parser -Version 1.0.2

## Implementation on example class :

    using FarDatetimeConverter.Converter;
    using Newtonsoft.Json;

    namespace Core.Manager
    {
        public class ExampleDTO
        {
            public ExampleDTO()
            {
            }

            [JsonProperty("exampleId")]
            public long ExampleId { get; set; }

            [JsonProperty("code")]
            public string Code { get; set; }

            [JsonConverter(typeof(FDateTimeConverter), "dd MMM yyyy HH:mm")]
            [JsonProperty("createdDate")]
            public System.DateTime CreatedDate { get; set; }
        }
    }


## MVC :
On mvc that make DateTime Converter work, you must add BaseController on your MVC Controller. You just put **JsonController** and using **FarDatetimeConverter.Mvc**.

    using FarDatetimeConverter.Mvc;
    using System.Web.Mvc;

    namespace FarstWeb.Controllers
    {
        public class ExamplesController : JsonController
        {
            // GET: Mahasiswas
            public ActionResult Index(long id)
            {
		var response = new object();
               // your code
               // your code
               return Json(response, JsonRequestBehavior.AllowGet);
            }
        }
    }


**EXPLAINATION**
> **[JsonConverter()]** : this base for us include our converter.  
> **typeof(FDateTimeConverter)** : add our converter.  
> **"dd MMM yyyy HH:mm"** : this is one of example our custom format date, you can add another format whatever you want.  
> if you don't take any custom format like **[JsonConverter(typeof(FDateTimeConverter)]** as default we make format **yyyyMMdd**.
