# Employee---management---system-
const express = require('express');
const router = express.Router();
const Employee = require('../models/Employee');

// Fetch all employee records
router.get('/employees', async (req, res) => {
    try {
        const employees = await Employee.find();
        res.status(200).json(employees);
    } catch (err) {
        res.status(500).json({ message: err.message });
    }
});

// Create new employee record
router.post('/employees', async (req, res) => {
    const employee = new Employee(req.body);
    try {
        const newEmployee = await employee.save();
        res.status(201).json(newEmployee);
    } catch (err) {
        res.status(400).json({ message: err.message });
    }
});

module.exports = router;
