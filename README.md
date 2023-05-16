DAY 7 TASKS

1.US Dollars

<!DOCTYPE html>
<html>
    <head>
        <title>Day 7 task</title>
    </head>
    <body>
        <h1>XMLHttpRequest</h1>
        <h3>Printing the country which uses US Dollars as currency</h3>
            <script>
                const req = new XMLHttpRequest()
                req.open("GET","https://restcountries.com/v3.1/all");
                req.send();
                req.responseType = 'json'
                req.onload =function(){
                   let data = req.response
                   let countries = data.filter((item)=>(item.currencies !== undefined))
                   let country = countries.filter((data)=>{
                    for(let key in data.currencies){
                        if(data.currencies[key].name === "United States dollar"){
                            return data
                        }
                    }
                   })
                   country.forEach(function(country) {
                        console.log(country.name.common);
                    });
                }
            </script>
    </body>
   
</html>


2.Asian countries

<!DOCTYPE html>
<html>
    <head>
        <title>Day 7 task</title>
    </head>
    <body>
        <h1>XMLHttpRequest</h1>
        <h3>Getting all the countries from the Asia continent /region using the Filter function</h3>
            <script>
                const req = new XMLHttpRequest()
                req.open("GET","https://restcountries.com/v3.1/all");
                req.responseType='json'
                req.send();
                req.onload = ()=>{
                    let responseObj = req.response
                    let cont = responseObj.filter(countries=>{
                        return countries.continents== "Asia"
                    })
                    let country = cont.map(countries=>{
                        return countries.name.common
                    })
                    console.log(country)
                }
                
                
            </script>
    </body>

</html>

3.For Each

<!DOCTYPE html>
<html>
    <head>
        <title>Day 7 task</title>
    </head>
    <body>
        <h1>XMLHttpRequest</h1>
        <h3>Printing name, capital, flag using forEach function</h3>
            <script>
                const xhr = new XMLHttpRequest();
                xhr.open('GET', 'https://restcountries.com/v3.1/all');
                xhr.responseType = 'json';
                xhr.onload = function() {
                var responseObj = xhr.response;
                responseObj.forEach(function(element) {
                console.log(element.flag);
                console.log(element.name.common);
                console.log(element.capital);
               });
               };
                xhr.send();

            </script>
    </body>

</html>

4.Population <2lakhs

<!DOCTYPE html>
<html>
    <head>
        <title>Day 7 task</title>
    </head>
    <body>
        <h1>XMLHttpRequest</h1>
        <h3> Getting all the countries with a population of less than 2 lakhs using Filter function</h3>
            <script>
                const req = new XMLHttpRequest()
                req.responseType = 'json'
                req.onload = function (){
                    let responseObj = req.response
                    let countries = responseObj.filter(function(countries){
                        return countries.population < 200000
                    })
                        countries.forEach(function(country) {
                            console.log(country.name.common)
                        });
                    }
                
                req.open("GET","https://restcountries.com/v3.1/all");
                req.send();

            </script>
    </body>

</html>

5.Total population

<!DOCTYPE html>
<html>
    <head>
        <title>Day 7 task</title>
    </head>
    <body>
        <h1>XMLHttpRequest</h1>
        <h3>Printing the total population of countries using reduce function</h3>
            <script>
                const req = new XMLHttpRequest()
                req.open("GET","https://restcountries.com/v3.1/all");
                req.send();
                req.responseType= 'json'
                req.onload = function(){
                    let responseObj= req.response
                   let population = responseObj.map(function(item){
                    return item.population
                   })
                   let totalPop = population.reduce(function(a,b){
                    return a+b
                   },0)
                   console.log(totalPop)
                }
            </script>
    </body>

</html>

