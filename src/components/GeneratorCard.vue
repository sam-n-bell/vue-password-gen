
<template>
    <v-card variant="tonal" >
        <v-card-title>
            Password Generator
        </v-card-title>
        <v-card-text>
            <div class="text-caption">Password Length</div>
            <v-slider v-model="passwordLength" thumb-label="always" min="8" max="25"></v-slider>
            <v-divider/>
            <v-checkbox v-model="includeNumbers" label="Include Numbers"/>
            <v-checkbox v-model="includeSymbols" label="Include Symbols"/>
            <v-divider/>
            <v-chip v-if="password != ''" variant="outlined" closable @click:close="clearPassword">
                {{ password }}
            </v-chip>
        </v-card-text>
        <v-card-actions>
            <v-btn v-if="password === ''" color="blue" variant="elevated" elevation="4" ripple @click="generatePasswordButton">Generate Password</v-btn>
            <v-btn v-else variant="elevated" elevation="4" @click="clearPassword" color="red">Clear Displayed</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
export default {
    data() {
        return {
            password: "",
            includeNumbers: true,
            includeSymbols: true,
            passwordLength: 20
        }
    },
    methods: {
        generatePasswordButton() {
            this.password = this.generatePassword(this.includeNumbers, this.includeSymbols, this.passwordLength)
        },
        clearPassword() {
            this.password = ""
        },
        getRandomLower() {
            return String.fromCharCode(Math.floor(Math.random() * 26) + 97);
        },
        getRandomNumber() {
            return String.fromCharCode(Math.floor(Math.random() * 10) + 48);
        },
        getRandomSymbol() {
            const symbols = "!@#$%^&*(){}[]=<>/,.";
            return symbols[Math.floor(Math.random() * symbols.length)];
        },
        generatePassword(includeNumbers, includeSymbols, passwordLength) {
            let generatedPassword = "";
            let variationsCount = [includeNumbers, includeSymbols].length;
            for (let i = 0; i < passwordLength; i += variationsCount) {
                if (includeNumbers) {
                    generatedPassword += this.getRandomNumber();
                }
                if (includeSymbols) {
                    generatedPassword += this.getRandomSymbol();
                }
                generatedPassword += this.getRandomLower();
            }
            const finalPassword = generatedPassword.slice(0, passwordLength);
            return finalPassword;
        }
    },
    mounted() {
        this.password = "";
    }
}
</script>
