<template>
    <div :style="backgroundStyle" class="background-container">
        <div class="container">
            <div class="hour"> {{ hour }}</div>
            <div class="dots"> : </div>
            <div class="minutes">{{ minutes }}</div>
            <div class="dots"> : </div>
            <div class="seconds"> {{ seconds }}</div>
            <div class="am-pm">{{ AmPm }} </div>
        </div>
    </div>
</template>

<script>
const ACCEPTED_VALUES = ["rainbow", "blue"]
export default {
    name: "HtmlClock",
    props: {
        theme: {
            type: String,
            validator: (value) => ACCEPTED_VALUES.includes(value)

        }
    },
    data() {
        return {
            hour: "",
            minutes: "",
            seconds: "",
            AmPm: ""
        }
    },
    mounted() {
        setInterval(() => {
            this.updateTime()
        }, 1000);
    },
    methods: {
        updateTime() {
            const date = new Date();

            let hour = date.getHours();
            let minutes = date.getMinutes();
            let seconds = date.getSeconds();

            this.hour = hour.toString().padStart(2, "0");
            this.minutes = minutes.toString().padStart(2, "0");
            this.seconds = seconds.toString().padStart(2, "0");

            if (hour > 12) {
                this.AmPm = "PM"
            } else {
                this.AmPm = "AM"
            }
        },
    }, computed: {
        backgroundStyle() {
            let backgroundColor;
            switch (this.theme) {
                case "rainbow":
                    backgroundColor = 'linear-gradient(to right, red, orange, yellow, green, blue, indigo, violet)';
                    break;
                case "blue":
                    backgroundColor = 'blue';
                    break;
                case "green":
                    backgroundColor = 'green';
                    break;
            }
            return {
                background: backgroundColor,
            }
        }
    },
}

</script>

<style scoped>
@keyframes appearDisappear {

    0%,
    100% {
        opacity: 0;
    }

    50% {
        opacity: 1;
    }
}

.container {
    width: 200px;
    font-size: 30px;
    background-color: black;
    color: red;
    padding: 15px;
    border-radius: 7px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.background-container {
    background-color: gray;
    width: fit-content;
    padding: 15px;
    margin: 0 auto;
}

.am-pm {
    margin-left: 10px;
    font-size: 10px;
    height: fit-content;
}

.dots {
    animation: appearDisappear 1s steps(1) infinite;
}
</style>