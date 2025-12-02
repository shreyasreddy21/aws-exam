1(j) display student GPA
<!DOCTYPE html>
<html>
<body>
<h3>Enter Student Details</h3>
<form id="studentForm" onsubmit="show(event)">
  Name: <input name="name"><br><br>
  Roll No: <input name="roll"><br><br>
  Subject1 Marks: <input name="m1"><br><br>
  Subject2 Marks: <input name="m2"><br><br>
  Subject3 Marks: <input name="m3"><br><br>
  <button type="submit">Submit</button>
</form>
<div id="data"></div>
<script>
function show(event) {
  event.preventDefault(); // Prevent page reload
  // Access form
  const form = document.getElementById("studentForm");
  // Get values from form fields
  let name = form.name.value;
  let roll = form.roll.value;
  let m1 = Number(form.m1.value);
  let m2 = Number(form.m2.value);
  let m3 = Number(form.m3.value);
  // Calculations
  let total = m1 + m2 + m3;
  let gpa = (total / 30).toFixed(2); // Assuming 100 marks → scale to 10
  // Output table
  let table = `
    <h3>Student Marks Sheet</h3>
    <table border='1'>
      <tr><td>Name</td><td>${name}</td></tr>
      <tr><td>Roll No</td><td>${roll}</td></tr>
      <tr><td>Subject 1</td><td>${m1}</td></tr>
      <tr><td>Subject 2</td><td>${m2}</td></tr>
      <tr><td>Subject 3</td><td>${m3}</td></tr>
      <tr><td>GPA</td><td>${gpa}</td></tr>
    </table>
  `;
  document.getElementById("data").innerHTML = table;
}
</script>
</body>
</html>



3) Node Js program that accepts port from the user(server.js)
var http = require('http');
var server = http.createServer(function (req, res){
    if (req.url == '/'){ //check the URL of the current request
        res.writeHead(200, { 'Content-Type': 'text/html' });
        //set response content
        res.write('<html><body><p>This is home Page.</p></body></html>');
        res.end();
    }
    else if (req.url == "/student") {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.write('<html><body><p>This is student Page.</p></body></html>');
        res.end();
    }
    else if (req.url == "/admin") {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.write('<html><body><p>This is admin Page.</p></body></html>');
        res.end();
    }
    else res.end('Invalid Request!');
});
server.listen(8000);
console.log('Node.js web server at port 8000 is running..')



7) create a form, based on roll number provided, the student details should be fetched(using ExpressJS)
