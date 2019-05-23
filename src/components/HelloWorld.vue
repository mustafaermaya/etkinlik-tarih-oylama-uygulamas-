<template>
  <div class="hello">
    <div class="table-responsive">
      <table class="table" style="text-align:center;">
        <tr>
          <td></td>
          <td>June</td>
        </tr>
        <tr>
          <td></td>
          <td v-for="day in days" :key="day">{{ day }}</td>
        </tr>
        <tr>
          <td>
            <input type="text" placeholder="Write Your Name" v-model="name">
            <button @click="save()">Kaydet</button>
          </td>
          <td>
            <input type="checkbox" v-model="selects.day1">
            <span>{{ submittedperson }} / {{ personnumber }}</span>
          </td>
          <td>
            <input type="checkbox" v-model="selects.day2">
            <span>{{ submittedperson }} / {{ personnumber }}</span>
          </td>
          <td>
            <input type="checkbox" v-model="selects.day3">
            <span>{{ submittedperson }} / {{ personnumber }}</span>
          </td>
          <td>
            <input type="checkbox" v-model="selects.day4">
            <span>{{ submittedperson }} / {{ personnumber }}</span>
          </td>
          <td>
            <input type="checkbox" v-model="selects.day5">
            <span>{{ submittedperson }} / {{ personnumber }}</span>
          </td>
          <td>
            <input type="checkbox" v-model="selects.day6">
            <span>{{ submittedperson }} / {{ personnumber }}</span>
          </td>
        </tr>
        <tr v-for="(person, index) in addedpersons" :key="index">
          <td>{{ person.name }}</td>
          <td>
            <input type="checkbox" value="checkbox1" :checked="person.day1" disabled="disabled">
          </td>
          <td>
            <input type="checkbox" value="checkbox2" :checked="person.day2" disabled="disabled">
          </td>
          <td>
            <input type="checkbox" value="checkbox3" :checked="person.day3" disabled="disabled">
          </td>
          <td>
            <input type="checkbox" value="checkbox4" :checked="person.day4" disabled="disabled">
          </td>
          <td>
            <input type="checkbox" value="checkbox5" :checked="person.day5" disabled="disabled">
          </td>
          <td>
            <input type="checkbox" value="checkbox6" :checked="person.day6" disabled="disabled">
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>


     

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      days: {
        first: "15 CT",
        second: "16  PZ",
        third: "22 CT",
        fourth: "23 PZ",
        fifth: "29 CT",
        sixth: "30 PZ"
      },
      selects: {
        day1: false,
        day2: false,
        day3: false,
        day4: false,
        day5: false,
        day6: false
      },
      personnumber: 8,
      submittedperson: 0,
      name: "",
      checkboxes: [],
      addedpersons: []
    };
  },
  methods: {
    save: function() {
      let obj = {
        name: this.name,
        day1: this.selects.day1,
        day2: this.selects.day2,
        day3: this.selects.day3,
        day4: this.selects.day4,
        day5: this.selects.day5,
        day6: this.selects.day6
      };
      if (this.name == "" || this.selects.day1 == false) {
        alert("You should write a name and check the boxes");
      } else {
        if (this.submittedperson !== this.personnumber) {
          this.submittedperson++;
          // this.addedpersons.push(this.name);
          this.addedpersons.push(obj);
        }
      }

      this.name = "";
      this.selects.day1 = false;
      this.selects.day2 = false;
      this.selects.day3 = false;
      this.selects.day4 = false;
      this.selects.day5 = false;
      this.selects.day6 = false;
    }
  },

  computed: {},
  watch: {
    submittedperson: function(value) {
      if (value > 8) {
        this.submittedperson = 8;
      }
    },
    addedpersons: function(value) {
      // if(addedpersons.length >8){

      // }
      console.log(value);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
