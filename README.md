API Login/Register и по-мелочи - https://mega.nz/file/oeVzRLIA#Aw61nXqSkzMh-fUKC1NgCgWt_EoQPjuu4_7lkNy3dag


sequelize.sync({ alter: true }).then(() => {
    app.listen(PORT, () => {
        console.log(`Server running on PORT:${PORT}`)
    })
})

index.js
require('dotenv').config();
const express = require('express');
const { sequelize } = require('./config/database');
const authRoutes = require('./routes/authRouter');
const doctorRoutes = require('./routes/doctorsRouter');

const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

app.use('/api/auth', authRoutes);
app.use('/api/doctors', doctorRoutes);


sequelize.sync({ alter: true }).then(() => {
    app.listen(PORT, () => {
        console.log(`Server running on PORT:${PORT}`)
    })
})
