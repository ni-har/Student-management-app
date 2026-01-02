const express = require('express');
const router = express.Router();

// Multiple student data
let students = [
    { id: 1, name: "Praveen", roll: "ECE101", dept: "ECE" },
    { id: 2, name: "Arun", roll: "CSE102", dept: "CSE" },
    { id: 3, name: "Divya", roll: "IT103", dept: "IT" }
];

// READ all students
router.get('/', (req, res) => {
    res.json(students);
});

// READ single student
router.get('/:id', (req, res) => {
    const student = students.find(s => s.id == req.params.id);
    student ? res.json(student) : res.status(404).send("Student not found");
});

// ADD student
router.post('/', (req, res) => {
    students.push(req.body);
    res.send("Student added successfully");
});

// UPDATE single student
router.put('/:id', (req, res) => {
    students = students.map(s =>
        s.id == req.params.id ? { ...s, ...req.body } : s
    );
    res.send("Student updated");
});

// UPDATE multiple students
router.put('/', (req, res) => {
    req.body.forEach(update => {
        students = students.map(s =>
            s.id == update.id ? { ...s, ...update } : s
        );
    });
    res.send("Multiple students updated");
});

// DELETE student
router.delete('/:id', (req, res) => {
    students = students.filter(s => s.id != req.params.id);
    res.send("Student deleted");
});

module.exports = router;
