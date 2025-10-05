# Controller Example
# Lab 5: HTTP Programming

## **Table of Contents**

- [Controller Example](#controller-example)
- [Lab 5: HTTP Programming](#lab-5-http-programming)
  - [**Table of Contents**](#table-of-contents)
    - [**StudentController.cs**](#studentcontrollercs)

### **StudentController.cs**

```csharp
/*
 **********************************
 * Author: Petar Kaselj
 * Project Task: University
 **********************************
 * Description:
 *  A program that has a list of all students in the university.
 *  The program has endpoints to:
 *      1. Get all students
 *      2. Get a specific student by his/her index in 3 different ways
 **********************************
 */

using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;

namespace pkaselj_lab_05_template.Controllers
{
    // Delete the line below !!!
    // [Route("api/[controller]")]
    [ApiController]
    public class StudentController : ControllerBase
    {
        // A sample list of students
        readonly IEnumerable<string> students = new[] { "Ante", "Ivo", "Mate" };

        // An endpoint that returns a list of all students
        // Postman request (example): GET http://localhost:5236/all-students
        // Postman response (example): ["Ante", "Ivo", "Mate"]
        [HttpGet]
        [Route("/all-students")]
        public IActionResult GetStudents()
        {
            return Ok(students);
        }

        // An endpoint that returns the name of a student at index `id` (index in an array `students`)
        // Postman request (example): GET http://localhost:5236/student/1
        // Postman response (example): "Ivo"
        //       * It returns "Ivo" because Ivo is at student[1] (see the top of the StudentController)
        [HttpGet]
        [Route("/student/{index}")]
        public IActionResult GetStudentByIndexFromRoute([FromRoute] int index)
        {
            // Check if `id` is larger that number of students
            // If you have 3 students ["Ante", "Ivo", "Mate"]
            // You only have 3 indices in the `student` array:
            //  student[0] = "Ante"
            //  student[1] = "Ivo"
            //  student[2] = "Mate"
            if (index < students.Count())
            {
                // `index` is valid (between 0 and 2)
                // Return 200 OK status and the name of the student at `index`
                return Ok( students.ElementAt(index) );
            }
            else
            {
                // `index` is invalid. For example, we have 3 students and `index` is 145
                // Return 400 Bad Request status code and a message
                return BadRequest($"Invalid index = {index}. There are only {students.Count()} students.");
            }
        }

        // An endpoint that returns the name of a student at index `id` (index in an array `students`)
        // Postman request (example): GET http://localhost:5236/student?index=1
        // Postman response (example): "Ivo"
        //       * It returns "Ivo" because Ivo is at student[1] (see the top of the StudentController)
        [HttpGet]
        [Route("/student")]
        public IActionResult GetStudentByIndexFromQuery([FromQuery] int index)
        {
            if (index < students.Count())
            {
                return Ok(students.ElementAt(index));
            }
            else
            {
                return BadRequest($"Invalid index = {index}. There are only {students.Count()} students.");
            }
        }

        // An endpoint that returns the name of a student at index `id` (index in an array `students`)
        // Postman request (example): POST http://localhost:5236/student
        //       * Set POST method
        //       * Go to Postman > Headers and add "Content-Type" header with value "application/json"
        //       * Go to Postman > Body and select "raw" and "text" and type '1' (WITHOUT the quotes)
        // Postman response (example): "Ivo"
        //       * It returns "Ivo" because Ivo is at student[1] (see the top of the StudentController)
        [HttpPost]
        [Route("/student")]
        public IActionResult GetStudentByIndexFromBody([FromBody] int index)
        {
            if (index < students.Count())
            {
                return Ok(students.ElementAt(index));
            }
            else
            {
                return BadRequest($"Invalid index = {index}. There are only {students.Count()} students.");
            }
        }
    }
}

```