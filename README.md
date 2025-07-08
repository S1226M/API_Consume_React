# API_Consume_React
# Download Cors and Axios
npm i cors  

npm i axios

# Add code in Program.cs in API project
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowReactApp",
        policy => policy.AllowAnyOrigin() 
                        .AllowAnyHeader()
                        .AllowAnyMethod());
});

# After build, run in API project in program.cs

app.UseCors("AllowReactApp");

# Make a JSX folder in react 

```csharp
import React, { useEffect, useState } from "react";
import axios from "axios";

export default function Country() {
  const [countries, setCountries] = useState([]);

  useEffect(() => {
    axios
      .get(----Enter Your API URL----------)
      .then((response) => {
        console.log("Countries fetched:", response.data);
        setCountries(response.data);
      })
      .catch((error) => {
        console.error("Error fetching countries:", error);
      });
  }, []);

  return (
    <div>
      <ul>
        {countries.map((country) => (
          <li>{country.countryName}</li>
        ))}
      </ul>
    </div>
  );
}

```
