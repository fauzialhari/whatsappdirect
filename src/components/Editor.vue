<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-lg-9 col-xl-8">
        <div class="row">
          <section class="col-12 col-lg-6 form">
            <div class="panel panel-default">
              <FormulateForm class="panel-body" @submit="onSubmit">
                <div class="row no-gutters align-items-start mb-2">
                  <div class="col-4">
                    <FormulateInput
                      v-model="country"
                      :options="{ '62': '+62 INA' }"
                      type="select"
                      label="Country code"
                      placeholder="Select an option"
                      class="line-nowrap"
                    />
                  </div>
                  <div class="col">
                    <FormulateInput
                      type="number"
                      v-model="phoneNumber"
                      label="Phone number"
                      placeholder="Phone"
                      validation="required"
                      ref="phone-number"
                    />
                  </div>
                </div>
                <div class="row">
                  <div class="col">
                    <FormulateInput
                      type="textarea"
                      v-model="message"
                      label="Enter your message (Optional)"
                      placeholder="Say hello"
                    />
                    <FormulateInput type="submit">
                      Send Message <span class="loader" />
                    </FormulateInput>
                  </div>
                </div>
              </FormulateForm>
            </div>
          </section>
          <div class="col-12 col-lg-6 copywriting mb-3">
            <h1>WhatsApp Direct</h1>
            <section>
              <h2>
                Send WhatsApp Message directly, without saving any contact!
              </h2>
              <p>
                Tired of saving one time contact? Because you just need to
                contact it once?<br />
                By through this page you will be able to WhatsApp them without
                hassle to save their contact. Just
                <a href="" @click.prevent="onClickInsertPhoneNumber"
                  >insert the phone number</a
                >
                and send your message directly,
                <i>without saving contact</i>.
              </p>
            </section>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Editor",
  data: function() {
    return {
      country: "62",
      phoneNumber: "",
      message: ""
    };
  },
  computed: {
    link() {
      return `https://api.whatsapp.com/send?phone=${this.country}${
        this.phoneNumber
      }${this.message ? `&text=${this.message}` : ""}`;
    }
  },
  methods: {
    onClickInsertPhoneNumber() {
      this.$refs[
        "phone-number"
      ].$el.children[0].children[1].children[0].focus();
    },
    onSubmit() {
      const link = document.createElement("a");
      link.href = this.link;
      link.target = "_blank";
      link.click();
    }
  }
};
</script>

<style lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

section.form {
  font-size: 1.5rem;

  .panel {
    margin-bottom: 20px;
    background-color: #fff;
    border: 1px solid transparent;
    border-radius: 4px;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
    border-color: #ddd;

    .panel-body {
      padding: 15px;
    }
  }
}

@media (max-width: 991.98px) {
  .copywriting {
    order: 0;
  }

  section.form {
    order: 1;
  }
}
</style>
