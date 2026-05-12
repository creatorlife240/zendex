# zendex const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

// Sample Data Structure for Zendex
let registry = [
    { id: 1, name: "Sample Entry", category: "General" }
];

// Routes
app.get('/', (req, res) => {
    res.send('Zendex API is running 🚀');
});

// Get all entries
app.get('/api/entries', (req, res) => {
    res.json(registry);
});

// Add a new entry
app.post('/api/entries', (req, res) => {
    const newEntry = req.body;
    registry.push(newEntry);
    res.status(201).json(newEntry);
});

app.listen(PORT, () => {
    console.log(`Server is live at http://localhost:${PORT}`);
});
