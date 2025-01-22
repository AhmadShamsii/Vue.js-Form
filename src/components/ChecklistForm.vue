<template>
    <div class="container my-4">
      <h2 class="text-center mb-4">New Care Support Worker Starter Pack</h2>
  
      <form @submit.prevent="handleSubmit">
        <section v-for="(section, sectionIndex) in checklist" :key="sectionIndex" class="mb-4">
          <h3 class="text-center">{{ section.title }}</h3>
          <table class="table table-bordered">
            <thead class="table-light">
              <tr>
                <th></th>
                <th></th>
                <th>DATE</th>
                <th>STAFF INITIALS</th>
                <th>STAFF SIGNATURE</th>
              </tr>
            </thead>
            <tbody>
              <template v-for="(item, itemIndex) in section.items" :key="itemIndex">
                <tr>
                  <td>{{ itemIndex + 1 }}</td>
                  <td>{{ item }}</td>
                  <td>
                    <input type="date" v-model="formData[sectionIndex][itemIndex].date" class="form-control" />
                  </td>
                  <td>
                    <input type="text" v-model="formData[sectionIndex][itemIndex].initials" class="form-control" />
                  </td>
                  <td>
                    <input type="text" v-model="formData[sectionIndex][itemIndex].signature" class="form-control" />
                  </td>
                </tr>
                <tr v-if="sectionIndex === 0 && itemIndex === section.items.length - 1">
                  <td colspan="5">
                    <label  for="comments">Comments:</label>
                    <textarea id="comments" v-model="comments" class="form-control"></textarea>
                  </td>
                </tr>
              </template>
            </tbody>
          </table>
        </section>
  
        <div class="text-center">
          <button type="button" class="btn btn-primary" @click="printChecklist">Print</button>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        checklist: [
          {
            title: "Pre-employment Checks",
            items: [
              "10-Year Employment History Form",
              "Ex-Employer Reference Received",
              "Character References Received",
              "DBS Authorisation Form Signed",
              "DBS Received",
              "NSW enrolled onto DBS Update Service",
              "Care Certificate Training Completed",
              "Moving and Handling Training",
              "Safer Handling Training",
            ],
          },
          {
            title: "Documentation",
            items: [
              "48 Hour Working Week Exemption Form",
              "Eligibility to Work in the UK Form",
              "Pre-Employment Medical Questionnaire",
              "Policies & Procedures Agreement Form",
              "Hours Availability Chart",
              "Emergency Contact Information",
              "Payroll Details",
              "Confidentiality Statement",
              "Contract of Employment",
            ],
          },
          {
            title: "Issuing of PPE and Uniform",
            items: [
              "ID Badge Issued",
              "Uniform Issued",
              "Uniform Agreement Form Signed",
              "PPE Issued",
            ],
          },
          {
            title: "Role Specific Matters – Care Coordinator",
            items: [
              "Welcome and Introduction",
              "Support Worker’s Role and Responsibilities",
              "Code of Conduct and Standards Expected",
              "Current Guidance on PPE",
              "Current Guidance on COVID-19 Testing",
              "Uniform Policy/Appearance & Dress Code",
              "Unable to Gain Entry to SUs Home",
            ],
          },
          {
            title: "BIRDIE MOBILE APPLICATION – OPERATIONAL",
            items: [
              "Birdie Mobile Downloaded",
              "Care Notes and Expectations",
              "Clocking-In and Out",
              "Viewing Shifts",
              "Geo-Location",
              "MAR Chart Recording and Codes",
            ],
          },
          {
            title: "Pay Related Matters – OPERATIONAL",
            items: [
              "Availability and Picking Up Hours and Shifts",
              "Pension Scheme",
              "Timesheets and Wage Slips",
              "Office Structure and Who to Contact",
            ],
          },
          {
            title: "DRIVERS - OPERATIONAL",
            items: [
              "Copy of Driver’s License",
              "Copy of Insurance Certificate",
              "Copy of MOT Certificate",
              "Mileage Allowances and Claims",
            ],
          },
        ],
        formData: [],
        comments: "",
      };
    },
    created() {
      this.formData = this.checklist.map(section =>
        section.items.map(() => ({ date: "", initials: "", signature: "" }))
      );
    },
    methods: {
      printChecklist() {
        window.print();
      },
      handleSubmit() {
        console.log("Form data submitted:", this.formData);
        alert("Form submitted successfully!");
      },
    },
  };
  </script>
  
  <style>
  @media print {
    button {
      display: none;
    }
    table {
      page-break-inside: avoid;
    }
  }
  
  h3 {
    margin-top: 20px;
    margin-bottom: 10px;
  }

  h1 {
    text-decoration: underline;
    font-weight: 100;
  }
  
  .table {
    font-size: 14px;
  }
  
  .table-bordered {
    border: 2px solid #dee2e6;
  }
  </style>
  