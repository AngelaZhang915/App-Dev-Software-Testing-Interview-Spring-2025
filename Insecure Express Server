const express = require("express");
const mongoose = require("mongoose");
const bodyParser = require("body-parser");
const cors = require("cors");

const app = express();
app.use(bodyParser.urlencoded({ extended: true }));
app.use(cors());

mongoose.connect("mongodb://localhost:27017/usersDB");

const UserSchema = new mongoose.Schema({
    username: String,
    password: String
});
const User = mongoose.model("User", UserSchema);

app.post("/login", async (req, res) => {
    const { username, password } = req.body;
    const user = await User.findOne({ username, password });
    if (user) {
        res.send("Login successful");
    } else {
        res.status(401).send("Unauthorized");
    }
});

app.delete("/deleteAllUsers", async (req, res) => {
    await User.deleteMany({});
    res.send("All users deleted");
});

app.listen(3000, () => {
    console.log("Server running on port 3000");
});
