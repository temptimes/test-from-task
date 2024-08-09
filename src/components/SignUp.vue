<template>
  <div class="sign-up">
    <div class="circle"></div>
    <div class="circle circle--bottom"></div>
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <v-card dark>
            <v-card-title>Sign Up for Free</v-card-title>
            <v-card-subtitle>
              Welcome, let’s get to know each other!
            </v-card-subtitle>
            <v-card-text>
              <v-form ref="form">
                <v-text-field
                  v-model="form.fullName"
                  :rules="fullNameRules"
                  placeholder="Enter your full name"
                  outlined
                  persistent-placeholder
                  hide-details="auto"
                  filled
                  dense
                  full-width
                >
                  <template #prepend>Full Name</template></v-text-field
                >
                <v-text-field
                  v-model="form.email"
                  :rules="emailRules"
                  placeholder="Enter your email"
                  outlined
                  persistent-placeholder
                  hide-details="auto"
                  filled
                  dense
                  full-width
                  ><template #prepend>Email</template><</v-text-field
                >
                <v-text-field
                  v-model="form.phoneNumber"
                  :rules="phoneNumberRules"
                  placeholder="Enter your phone number"
                  outlined
                  persistent-placeholder
                  hide-details="auto"
                  filled
                  dense
                  full-width
                  ><template #prepend>Phone number</template></v-text-field
                >
                <div class="sign-up__buttons">
                  <v-col cols="12">
                    <v-btn
                      block
                      height="52px"
                      color="rgb(255, 255, 255)"
                      class="button button--primary"
                      @click="submit"
                      >Continue</v-btn
                    >
                  </v-col>
                  <v-col cols="12">
                    <v-btn
                      block
                      height="52px"
                      color="rgba(39, 39, 41, 0.3)"
                      class="button button--secondary"
                      >I have an account</v-btn
                    >
                  </v-col>
                </div>
              </v-form>
            </v-card-text>
            <v-card-actions>
              <v-row>
                <v-col cols="12">
                  <p class="sign-up__terms">
                    <span>
                      By signing up, you agree to the
                      <a class="sign-up__terms-link" href="#"
                        >Terms of Service</a
                      >
                      and
                      <a class="sign-up__terms-link" href="#">Privacy Policy</a
                      >.
                    </span>
                  </p>
                </v-col>
              </v-row>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "SignUp",
  data() {
    return {
      form: {
        fullName: "",
        email: "",
        phoneNumber: "",
      },
      fullNameRules: [
        (v) => !!v || "Full Name is required",
        (v) =>
          (v && v.length >= 3) || "Full Name must be at least 3 characters",
      ],
      emailRules: [
        (v) => !!v || "Email is required",
        (v) => /.+@.+\..+/.test(v) || "Email must be valid",
      ],
      phoneNumberRules: [
        (v) => !!v || "Phone number is required",
        (v) => /^\d{10}$/.test(v) || "Phone number must be 10 digits",
      ],
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        alert("Form submitted!");
      }
    },
  },
};
</script>

<style lang="scss" scroped>
@import "@/assets/styles/main.scss";

.sign-up {
  position: relative;
  height: 100vh;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;

  .circle {
    top: -851px;
    left: -613px;
    &--bottom {
      top: auto;
      left: auto;
      bottom: -1051px;
      right: -813px;
    }
  }

  &__buttons {
    margin-top: 32px;
    .button {
      &--secondary {
        margin-top: 12px;
      }
    }
  }

  &__terms {
    font-size: $text-xxs;
    font-weight: 400;
    color: rgba(149, 150, 157, 1);
    display: flex;
    justify-content: center;
    text-align: center;
  }

  &__terms-link {
    color: rgba(245, 245, 246, 1);
    &:hover {
      opacity: 0.7;
    }
  }

  .container {
    z-index: 10;
    text-align: center;
    .row {
      display: flex;
      align-items: center;
      justify-content: center;
      .theme--dark {
        background-color: transparent;
      }

      .v-sheet {
        position: relative;
        max-width: 600px;
        padding: 52px 32px 0px 32px;
        border-top-left-radius: 12px;
        border-top-right-radius: 12px;
        overflow: hidden;
        border-top: 1px solid #86888f;
        box-shadow: none;

        &::after,
        &::before {
          content: "";
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          pointer-events: none;
          box-sizing: border-box;
        }

        &::before {
          border-left: 1px solid transparent;
          border-image: linear-gradient(
            to bottom,
            #86888f 30%,
            transparent 70%
          );
          border-image-slice: 1;
        }

        &::after {
          border-right: 1px solid transparent;
          border-image: linear-gradient(
            to bottom,
            #86888f 20%,
            transparent 45%
          );
          border-image-slice: 1;
        }
      }

      .v-card {
        &__title {
          justify-content: center;
          font-size: $text-xl;
          padding: 2px;
          background: linear-gradient(to left, #f5f5f6 20%, #95969d 100%);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
          font-weight: 500;
        }

        &__subtitle {
          font-size: $text-base;
          color: #c2c2c6;
          padding: 0;
          margin-top: 8px;
        }

        &__text {
          padding: 32px 0 48px 0;
        }
      }

      .v-input {
        display: flex;
        flex-direction: column;
        border-radius: 8px;
        margin-bottom: 20px;

        .v-input__prepend-outer {
          margin-bottom: 8px;
          font-size: $text-base;
          letter-spacing: 0.15;
          color: #f5f5f6;
        }

        &:hover {
          fieldset {
            border-color: #808080;
          }
        }

        fieldset {
          border-color: #333741;
        }

        &.v-input--is-focused {
          fieldset {
            border: 2px solid #cccccc;
          }
        }

        &__slot {
          height: 48px;
          margin-bottom: 0;
          background-color: #27272926;

          &:hover {
            background: #27272926 !important;
          }
          .v-text-field {
            &__slot {
              font-size: $text-base;
              color: #f5f5f6;

              input {
                &::placeholder {
                  color: #a2a3a9;
                  font-size: $text-base;
                }
              }
            }
          }
        }

        &__control {
          position: relative;
          .v-text-field {
            &__details {
              padding: 0;
              margin: 0;
              position: absolute;
              bottom: -18px;
            }
          }
        }
      }
    }
  }
}
</style>
