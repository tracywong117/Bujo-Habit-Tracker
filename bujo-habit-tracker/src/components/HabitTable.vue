<template>
    <div class="habit-tracker">
        <h1>Habit Tracker</h1>
        <table>
            <thead>
                <tr>
                    <th></th>
                    <th v-for="day in days" :key="day">{{ day }}</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(habit, index) in habits" :key="index">
                    <td>{{ habit.name }}</td>
                    <td v-for="(status, dayIndex) in habit.status" :key="dayIndex">
                        <!-- <input class="custom-checkbox" type="checkbox" v-model="habit.status[dayIndex]" /> -->
                        <label class="custom-checkbox">
                            <input type="checkbox" v-model="habit.status[dayIndex]" />
                            <span class="checkmark"></span>
                            <span class="circle"></span>
                        </label>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            days: Array.from({ length: 31 }, (_, i) => i + 1),
            habits: [
                { name: "exercise", status: Array(31).fill(false) },
                { name: "vitamins", status: Array(31).fill(false) },
                { name: "read book", status: Array(31).fill(false) },
                { name: "journal", status: Array(31).fill(false) },
            ],
        };
    },
};
</script>

<style scoped>
.habit-tracker {
    font-family: Arial, sans-serif;
    margin: 20px;
    text-align: center;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
}

th,
td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
}

th {
    background-color: #f2f2f2;
}

input[type="checkbox"] {
    transform: scale(1.2);
}
</style>
