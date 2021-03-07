# TABLES 

When representing information in a table, you need to think in terms of a grid made up of rows and columns (a bit like aspreadsheet).

**A table** represents information in a grid format. Examples of tables include financial reports, TV schedules, and sports results 

![table](https://ictacademy.com.ng/wp-content/uploads/2017/10/HTML-Table-Structure.png)

```
- The <table> element is used to add tables to a web page.
- A table is drawn out row by row. Each row is created with the <tr> element.
- Inside each row there are a number of cells represented by the <td> element (or <th> if it is a header).
- You can make cells of a table span more than one row or column using the rowspan and colspan attributes.
- For long tables you can split the table into a <thead>, <tbody>, and <tfoot>
```

![s](https://3.bp.blogspot.com/-7oKODJ6Qukw/W09i8ZxgGvI/AAAAAAAANeY/5pTuMPjFe5MzFthszYkSAplK3m5OsfUiQCLcBGAs/s1600/111.jpg)


# Functions, Methods, and Objects 

Functions let you group a series of statements together to perform a specific task. If different parts of a script repeat the same task, you can
reuse the function (rather than repeating the same set of statements). 

![ss](http://01eba9f59936628a9c10-a672e330d72d3d2e689cb64015c1f8c5.r97.cf2.rackcdn.com/set-3.jpg)

```
- Functions allow you to group a set of related statements together that represent a single task
- Functions can take parameters (informatiorJ required to do their job) and may return a value.
- An object is a series of variables and functions that represent something from the world around you.
- In an object, variables are known as properties of the object; functions are known as methods of the object. 
- Web browsers implement objects that represent both the browser window and the document loaded into the browser window.
- JavaScript also has several built-in objects such as String, Number, Math, and Date. Their properties and 
- methods offer functionality that help you write scripts.
- Arrays and objects can be used to create complex data sets (and both can contain the other). 

```


 methods can be added to a constructor function's **prototype**. Think of the prototype as an object's stunt double. Whenever a scene is too dangerous, you can substitute in the prototype to do the work while the object takes all the glory
 ```javascript
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail.generateRandom(1, 5));
console.log(corgiFail.generateRandom(1, 5));
```
[source](https://github.com/codefellows/domain_modeling#domain-modeling)
