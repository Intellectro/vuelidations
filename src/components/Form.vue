<template>
    <div :style="{ flex: size }" class="form-container">
        <div class="form-contents">
            <div class="title">Create Account</div>
            <Form action="#" @submit="onSubmit" class="form">
                <div class="input-box">
                    <label for="firstname">First Name</label>
                    <div class="row-up">
                        <ErrorMessage name="firstname" class="error-msg" />
                        <div class="input-icon">
                            <Field
                                name="firstname"
                                type="text"
                                class="firstname"
                                :rules="validateFirst" />
                            <i class="fa fa-user"></i>
                        </div>
                    </div>
                </div>
                <div class="input-box">
                    <label for="lastname">Last Name</label>
                    <div class="row-up">
                        <ErrorMessage name="lastname" class="error-msg" />
                        <div class="input-icon">
                            <Field
                                name="lastname"
                                type="text"
                                :rules="validateLast"
                                class="lastname" />
                            <i class="fa fa-user"></i>
                        </div>
                    </div>
                </div>
                <div class="input-box">
                    <label for="phonenumber">Phone Number</label>
                    <div class="row-up">
                        <ErrorMessage name="phone" class="error-msg" />
                        <div class="input-icon">
                            <Field
                                name="phone"
                                type="tel"
                                :rules="validatePhone"
                                class="phone" />
                            <i class="fa fa-mobile"></i>
                        </div>
                    </div>
                </div>
                <div class="input-box">
                    <label for="email">Email Address</label>
                    <div class="row-up">
                        <ErrorMessage name="email" class="error-msg" />
                        <div class="input-icon">
                            <Field
                                name="email"
                                :rules="validateEmail"
                                type="email"
                                class="email" />
                            <i class="fa fa-envelope"></i>
                        </div>
                    </div>
                </div>
                <div class="input-box">
                    <label for="password">Password</label>
                    <div class="row-up">
                        <ErrorMessage name="password" class="error-msg" />
                        <div class="input-icon">
                            <Field
                                :rules="validatePassowrd"
                                name="password"
                                type="password"
                                class="password" />
                            <i class="fa fa-key"></i>
                        </div>
                    </div>
                </div>
                <button class="submit-btn" type="submit">Submit</button>
            </Form>
        </div>
    </div>
</template>

<script>
import { Form, Field, ErrorMessage } from "vee-validate";

function setSuccess(element) {
    element.style.border = "0.95px solid green";
}

export default {
    name: "Formval",
    props: ["size"],
    methods: {
        onSubmit() {
            let firstname = document.querySelector(".firstname");
            let lastname = document.querySelector(".lastname");
            let phone = document.querySelector(".phone");
            let email = document.querySelector(".email");
            let password = document.querySelector(".password");

            if (
                firstname.value &&
                lastname.value &&
                phone.value &&
                email.value &&
                password.value
            ) {
                alert("Data sent successfully");
                document.querySelectorAll("input").forEach((input) => {
                    input.value = "";
                });
            }
        },

        validateFirst(value) {
            const firstborder = document.querySelector(".firstname");
            const namecheck = /([\s\d]+)/;
            if (!value) {
                return "this input form is required";
            } else if (namecheck.test(value)) {
                firstborder.style.border = "0.95px solid red";
                return "Please enter a valid name";
            } else {
                setSuccess(firstborder);
                return true;
            }
        },

        validateLast(value) {
            const lastborder = document.querySelector(".lastname");
            const namecheck = /([\s\d]+)/;
            if (!value) {
                return "this input form is required";
            } else if (namecheck.test(value)) {
                lastborder.style.border = "0.95px solid red";
                return "Please enter a valid name";
            } else {
                setSuccess(lastborder);
                return true;
            }
        },

        validateEmail(value) {
            const emailborder = document.querySelector(".email");
            const emailcheck = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
            if (!value) {
                return "this input form is required";
            }
            if (!emailcheck.test(value)) {
                emailborder.style.border = "0.95px solid red";
                return "This field must be a valid email";
            }
            setSuccess(emailborder);
            return true;
        },

        validatePhone(value) {
            const inputBorder = document.querySelector(".phone");
            const phonecheck = /([a-z]+)/;
            if (!value) {
                return "this input form is required";
            } else if (phonecheck.test(value)) {
                inputBorder.style.border = "0.95px solid red";
                return "this field must be a valid phone number";
            } else {
                setSuccess(inputBorder);
                return true;
            }
        },

        validatePassowrd(value) {
            const passborder = document.querySelector(".password");
            if (!value) {
                return "this input form is required";
            } else if (value.length < 8) {
                passborder.style.border = "0.95px solid red";
                return "passowrd must be at least 8 characters";
            } else {
                setSuccess(passborder);
                return true;
            }
        },
    },
    components: {
        Form,
        Field,
        ErrorMessage,
    },
};
</script>

<style scope>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500&family=Poppins:wght@100;200;300;400&display=swap");
.form-container {
    height: 100%;
}

.form-contents {
    padding: 30px 5%;
}

.form-container * {
    font-family: "Poppins", sans-serif;
}

.title {
    font-size: 40px;
    font-weight: 600;
    margin-bottom: 20px;
}

.form {
    display: flex;
    flex-direction: column;
    row-gap: 13px;
}

.input-box {
    display: flex;
    flex-direction: column;
    row-gap: 6px;
}

.input-icon input {
    width: 100%;
    padding: 8px;
    border-radius: 9px;
    border-width: thin;
}

.input-icon input:focus {
    outline: none;
}

.submit-btn {
    align-self: center;
    margin-top: 7px;
    min-width: 140px;
    padding: 13px;
    font-weight: bold;
    border: none;
    background-color: #19467d;
    color: white;
    cursor: pointer;
    border-radius: 8px;
}

.row-up {
    display: flex;
    flex-direction: column-reverse;
}

.error-msg {
    font-size: 11px;
    color: red;
    text-align: right;
}

.error-msg ~ .input-icon input {
    border: 0.95px solid red;
}
</style>
