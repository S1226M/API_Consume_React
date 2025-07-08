# API_Consume_React
# Download Cors and Axios
npm i cors  

npm i axios

# Add code in Program.cs 
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowReactApp",
        policy => policy.AllowAnyOrigin()  // <-- React app origin
                        .AllowAnyHeader()
                        .AllowAnyMethod());
});

# After build, run
app.UseCors("AllowReactApp");

# Make a JSX folder in react 
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
