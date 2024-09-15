<template>
  <!-- Top navigation -->
  <div class="breadcrumbs text-sm p-4 bg-slate-50">
    <ul>
      <li>
        <a>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 me-2"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
            />
          </svg>
          Bansos
        </a>
      </li>
      <li>
        <a>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="h-4 w-4 stroke-current me-2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-6l-2-2H5a2 2 0 00-2 2z"
            ></path>
          </svg>
          Data
        </a>
      </li>
      <li>
        <span class="inline-flex items-center gap-2">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="h-4 w-4 stroke-current"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M9 13h6m-3-3v6m5 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
            ></path>
          </svg>
          Registrasi
        </span>
      </li>
    </ul>
  </div>
  <!-- Main Content -->
  <div class="bansos-form p-4 max-w-2xl mx-auto">
    <!-- Header -->
    <div class="breadcrumbs mb-4 mt-10">
      <ul>
        <li class="text-2xl font-bold lg:text-4xl lg:font-normal">
          Bantuan Sosial
        </li>
        <li class="lg:text-2xl font-normal text-gray-400">Pendaftaran</li>
      </ul>
    </div>

    <!-- Form -->
    <form @submit.prevent="handleSubmit" class="flex flex-col space-y-4">
      <!-- Name Field -->
      <div class="join">
        <label
          for="name"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Nama</p>
        </label>
        <input
          type="text"
          id="name"
          v-model="form.name"
          class="input input-bordered join-item w-full"
          placeholder="Nama lengkap anda"
          required
        />
      </div>

      <!-- NIK Field -->
      <div class="join">
        <label
          for="nik"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">NIK</p>
        </label>
        <input
          type="number"
          id="nik"
          v-model="form.nik"
          class="input input-bordered join-item w-full"
          placeholder="Masukkan NIK anda"
          required
        />
      </div>

      <!-- KK Number Field -->
      <div class="join">
        <label
          for="familyCard"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Nomor KK</p>
        </label>
        <input
          type="number"
          id="familyCard"
          v-model="form.familyCard"
          class="input input-bordered w-full join-item"
          placeholder="Masukkan Nomor KK"
          required
        />
      </div>

      <div class="space-y-6">
        <!-- File field  -->
        <div role="alert" class="alert shadow-lg">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="stroke-info h-6 w-6 shrink-0 self-start"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
            ></path>
          </svg>
          <div>
            <h3 class="font-bold">Instruksi!</h3>
            <div class="text-xs">Maksimal 2MB, format JPG/JPEG/PNG/BMP</div>

            <div>
              <label for="ktpPhoto" class="form-control w-full">
                <div class="label">
                  <span class="font-bold text-slate-700">Foto KTP</span>
                </div>
                <input
                  type="file"
                  id="ktpPhoto"
                  ref="ktpPhoto"
                  @change="handleFileUpload('ktpPhoto', $event)"
                  accept="image/*"
                  class="file-input file-input-bordered w-auto"
                  required
                />
              </label>
            </div>

            <div>
              <label for="familyCardPhoto" class="form-control w-full">
                <div class="label">
                  <span class="font-bold text-slate-700"
                    >Foto Kartu Keluarga</span
                  >
                </div>
                <input
                  type="file"
                  id="familyCardPhoto"
                  ref="familyCardPhoto"
                  @change="handleFileUpload('familyCardPhoto', $event)"
                  accept="image/*"
                  class="file-input file-input-bordered w-auto"
                  required
                />
              </label>
            </div>
          </div>
        </div>

        <!-- Age and Gender field in the same row -->
        <div class="flex gap-4">
          <div class="join w-1/2">
            <label for="age" class="join-item btn bg-gray-300 w-1/2">
              <p class="font-bold text-slate-700">Umur</p>
            </label>
            <input
              type="number"
              id="age"
              v-model="form.age"
              class="join-item input input-bordered w-full"
              min="25"
              required
            />
          </div>

          <div class="flex flex-col w-1/4">
            <label for="gender" class="block font-bold text-slate-700 mb-2"
              >Jenis Kelamin:</label
            >
            <div class="form-control">
              <label class="label cursor-pointer">
                <span class="label-text">Laki-laki</span>
                <input
                  type="radio"
                  name="gender"
                  v-model="form.gender"
                  value="Laki-laki"
                  class="radio checked:bg-blue-500"
                  required
                />
              </label>
            </div>
            <div class="form-control">
              <label class="label cursor-pointer">
                <span class="label-text">Perempuan</span>
                <input
                  type="radio"
                  name="gender"
                  v-model="form.gender"
                  value="Perempuan"
                  class="radio checked:bg-pink-500"
                  required
                />
              </label>
            </div>
          </div>
        </div>
      </div>

      <!-- Province field  -->
      <div class="join">
        <label
          for="province"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Provinsi</p>
        </label>
        <select
          id="province"
          v-model="form.province"
          @change="fetchCities"
          class="join-item select select-bordered w-full"
          required
        >
          <option
            v-for="province in provinces"
            :key="province.id"
            :value="province.name"
          >
            {{ province.name }}
          </option>
          <option value="Other">Lainnya</option>
        </select>
        <input
          v-if="form.province === 'Other'"
          type="text"
          v-model="form.customProvince"
          placeholder="Isi provinsi"
          class="input input-bordered w-full ms-2"
        />
      </div>

      <!-- Regencies field -->
      <div class="join">
        <label
          for="city"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Kab/ Kota</p>
        </label>

        <select
          id="city"
          v-model="form.city"
          @change="fetchSubDistricts"
          class="join-item select select-bordered w-full"
          required
        >
          <option v-for="city in cities" :key="city.id" :value="city.name">
            {{ city.name }}
          </option>
          <option value="Other">Lainnya</option>
        </select>
        <input
          v-if="form.city === 'Other'"
          type="text"
          v-model="form.customCity"
          placeholder="Isi kabupaten/kota"
          class="input input-bordered w-full ms-2"
        />
      </div>

      <!-- Sub District Field -->
      <div class="join">
        <label
          for="subDistrict"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Kecamatan</p>
        </label>
        <select
          id="subDistrict"
          v-model="form.subDistrict"
          @change="fetchVillages"
          class="join-item select select-bordered w-full"
          required
        >
          <option
            v-for="subDistrict in subDistricts"
            :key="subDistrict.id"
            :value="subDistrict.name"
          >
            {{ subDistrict.name }}
          </option>
          <option value="Other">Lainnya</option>
        </select>
        <input
          v-if="form.subDistrict === 'Other'"
          type="text"
          v-model="form.customSubDistrict"
          placeholder="Isi kecamatan"
          class="input input-bordered w-full ms-2"
        />
      </div>

      <!-- Village Field -->
      <div class="join">
        <label
          for="village"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Kel/ Desa</p>
        </label>
        <select
          id="village"
          v-model="form.village"
          class="join-item select select-bordered w-full"
          required
        >
          <option
            v-for="village in villages"
            :key="village.id"
            :value="village.name"
          >
            {{ village.name }}
          </option>
          <option value="Other">Lainnya</option>
        </select>
        <input
          v-if="form.village === 'Other'"
          type="text"
          v-model="form.customVillage"
          placeholder="Isi kelurahan/desa"
          class="input input-bordered w-full ms-2"
        />
      </div>

      <!-- Address Field -->
      <div class="join">
        <label
          for="address"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Alamat</p>
        </label>
        <input
          type="text"
          id="address"
          v-model="form.address"
          class="join-item input input-bordered w-full"
          maxlength="255"
          required
        />
      </div>

      <div class="flex gap-4 w-full">
        <div class="join w-1/2">
          <label
            for="rt"
            class="join-item flex items-center justify-end bg-gray-300 w-1/2"
          >
            <p class="font-bold text-slate-700 me-2">RT</p>
          </label>
          <input
            type="text"
            id="rt"
            v-model="form.rt"
            class="join-item input input-bordered w-full"
          />
        </div>
        <div class="join w-1/2">
          <label
            for="rw"
            class="join-item flex items-center justify-end bg-gray-300 w-1/2"
          >
            <p class="font-bold text-slate-700 me-2">RW</p>
          </label>
          <input
            type="text"
            id="rw"
            v-model="form.rw"
            class="join-item input input-bordered w-full"
          />
        </div>
      </div>

      <div>
        <label
          for="incomeBeforePandemic"
          class="block text-sm font-medium text-gray-700"
          >Penghasilan sebelum pandemi:</label
        >
        <input
          type="number"
          id="incomeBeforePandemic"
          v-model="form.incomeBeforePandemic"
          class="input input-bordered w-full"
          required
        />
      </div>

      <div>
        <label
          for="incomeAfterPandemic"
          class="block text-sm font-medium text-gray-700"
          >Penghasilan setelah pandemi:</label
        >
        <input
          type="number"
          id="incomeAfterPandemic"
          v-model="form.incomeAfterPandemic"
          class="input input-bordered w-full"
          required
        />
      </div>

      <div>
        <label for="reason" class="block text-sm font-medium text-gray-700"
          >Alasan membutuhkan bantuan:</label
        >
        <select
          id="reason"
          v-model="form.reason"
          class="select select-bordered w-full"
          required
        >
          <option value="Kehilangan pekerjaan">Kehilangan pekerjaan</option>
          <option value="Kepala keluarga">Kepala keluarga</option>
          <option value="Tergolong fakir/miskin">Tergolong fakir/miskin</option>
          <option value="Other">Lainnya</option>
        </select>
        <input
          v-if="form.reason === 'Other'"
          type="text"
          v-model="form.customReason"
          placeholder="Isi alasan"
          class="input input-bordered w-full mt-2"
        />
      </div>

      <div class="flex items-center">
        <input
          type="checkbox"
          id="declaration"
          v-model="form.declaration"
          class="checkbox checkbox-primary mr-2"
          required
        />
        <label for="declaration" class="text-sm text-gray-700">
          Saya menyatakan bahwa data yang diisikan adalah benar dan siap
          mempertanggungjawabkan apabila ditemukan ketidaksesuaian dalam data
          tersebut.
        </label>
      </div>

      <button type="submit" class="btn btn-primary w-full" :disabled="loading">
        {{ loading ? "Submitting..." : "Submit" }}
      </button>
    </form>

    <div v-if="submitted" class="mt-4 p-4 bg-green-100 text-green-700 rounded">
      <h3 class="text-lg font-semibold">Form Submitted Successfully</h3>
      <pre>{{ form }}</pre>
    </div>
    <div v-if="error" class="mt-4 p-4 bg-red-100 text-red-700 rounded">
      <p>{{ errorMessage }}</p>
    </div>
  </div>

  <!-- Footer -->
  <footer class="footer footer-center bg-base-300 text-base-content p-4">
    <aside>
      <p>Copyright © 2024 - All right reserved by Daffa Ulhaq</p>
    </aside>
  </footer>
</template>

<script>
import axios from "axios";
import Swal from "sweetalert2";

export default {
  data() {
    return {
      form: {
        name: "",
        nik: "",
        familyCard: "",
        ktpPhoto: null,
        familyCardPhoto: null,
        age: 0,
        gender: "",
        province: "",
        customProvince: "",
        city: "",
        customCity: "",
        subDistrict: "",
        customSubDistrict: "",
        village: "",
        customVillage: "",
        address: "",
        rt: "",
        rw: "",
        incomeBeforePandemic: 0,
        incomeAfterPandemic: 0,
        reason: "",
        customReason: "",
        declaration: false,
      },
      provinces: [],
      cities: [],
      subDistricts: [],
      villages: [],
      submitted: false,
      loading: false,
      error: false,
      errorMessage: "",
    };
  },
  methods: {
    handleFileUpload(field, event) {
      const file = event.target.files[0];
      if (file) {
        if (file.size <= 2 * 1024 * 1024) {
          this.form[field] = file;
        } else {
          const Toast = Swal.mixin({
            toast: true,
            position: "center",
            iconColor: "white",
            customClass: {
              popup: "colored-toast",
            },
            showConfirmButton: false,
            timer: 3000,
            timerProgressBar: true,
          });
          Toast.fire({
            icon: "error",
            title: "Ukuran foto melebihi 2MB",
          });
          this.$refs[field].value = null; // Clear the file input
          this.form[field] = null; // Clear the file field
        }
      }
    },
    async handleSubmit() {
      Swal.fire({
        title: "Periksa kembali data anda",
        html: `
    <div class="space-y-4">
      <div class="join w-full">
        <label for="name" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Nama</p>
        </label>
        <input
          type="text"
          id="name"
          value="${this.form.name}"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      
      <div class="join w-full">
        <label for="nik" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">NIK</p>
        </label>
        <input
          type="text"
          id="nik"
          value="${this.form.nik}"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      
      <div class="join w-full">
        <label for="familyCard" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">No. KK</p>
        </label>
        <input
          type="text"
          id="familyCard"
          value="${this.form.familyCard}"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      
      <div class="join w-full">
        <label for="age" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Umur</p>
        </label>
        <input
          type="number"
          id="age"
          value="${this.form.age}"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      
      <div class="join w-full">
        <label for="gender" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Jenis Kelamin</p>
        </label>
        <input
          type="text"
          id="gender"
          value="${this.form.gender}"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      
      <div class="join w-full">
        <label for="province" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Provinsi</p>
        </label>
        <input
          type="text"
          id="province"
          value="${
            this.form.province === "Other"
              ? this.form.customProvince
              : this.form.province
          }"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      <div class="join w-full">
        <label for="province" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Provinsi</p>
        </label>
        <input
          type="text"
          id="province"
          value="${
            this.form.province === "Other"
              ? this.form.customProvince
              : this.form.province
          }"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      <div class="join w-full">
        <label for="city" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Kota</p>
        </label>
        <input
          type="text"
          id="city"
          value="${
            this.form.city === "Other" ? this.form.customCity : this.form.city
          }"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      <div class="join w-full">
        <label for="subdistrict" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Kecamatan</p>
        </label>
        <input
          type="text"
          id="subdistrict"
          value="${
            this.form.subDistrict === "Other"
              ? this.form.customSubDistrict
              : this.form.subDistrict
          }"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      <div class="join w-full">
        <label for="village" class="join-item flex items-center justify-end bg-gray-300 w-1/2">
          <p class="font-bold text-slate-700 me-2">Desa</p>
        </label>
        <input
          type="text"
          id="village"
          value="${
            this.form.village === "Other"
              ? this.form.customVillage
              : this.form.village
          }"
          class="input input-bordered input-md join-item w-full"
          disabled
        />
      </div>
      <div class="join w-full">
        <label
          for="address"
          class="join-item flex items-center justify-end bg-gray-300 w-1/2"
        >
          <p class="font-bold text-slate-700 me-2">Alamat</p>
        </label>
        <input
          type="text"
          id="address"
          value="${this.form.address}"
          class="join-item input input-bordered w-full"
          disabled
        />
      </div>

      <div class="flex gap-4 w-full">
        <div class="join w-1/2">
          <label
            for="rt"
            class="join-item flex items-center justify-end bg-gray-300 w-1/2"
          >
            <p class="font-bold text-slate-700 me-2">RT</p>
          </label>
          <input
            type="text"
            id="rt"
            value="${this.form.rt}"
            class="join-item input input-bordered w-full"
            disabled
          />
        </div>
        <div class="join w-1/2">
          <label
            for="rw"
            class="join-item flex items-center justify-end bg-gray-300 w-1/2"
          >
            <p class="font-bold text-slate-700 me-2">RW</p>
          </label>
          <input
            type="text"
            id="rw"
            value="${this.form.rw}"
            class="join-item input input-bordered w-full"
            disabled
          />
        </div>
      </div>

      <div>
        <label
          for="incomeBeforePandemic"
          class="block text-sm font-medium text-gray-700"
          >Penghasilan sebelum pandemi:</label
        >
        <input
          type="number"
          id="incomeBeforePandemic"
          value="${this.form.incomeBeforePandemic}"
          class="input input-bordered w-full"
          disabled
        />
      </div>

      <div>
        <label
          for="incomeAfterPandemic"
          class="block text-sm font-medium text-gray-700"
          >Penghasilan setelah pandemi:</label
        >
        <input
          type="number"
          id="incomeAfterPandemic"
          value="${this.form.incomeAfterPandemic}"
          class="input input-bordered w-full"
          disabled
        />
      </div>

      <div>
        <label for="reason" class="block text-sm font-medium text-gray-700"
          >Alasan membutuhkan bantuan:</label
        >
        <input
          type="text"
          id="reason"
          value="${
            this.form.reason === "Other"
              ? this.form.customReason
              : this.form.reason
          }"
          class="input input-bordered w-full"
          disabled
        />
      </div>

      <!-- Gambar KTP -->
      <div class="flex flex-col items-center gap-2">
        <p class="font-bold text-slate-700">Foto KTP</p>
        <img 
          src="${
            this.form.ktpPhoto ? URL.createObjectURL(this.form.ktpPhoto) : ""
          }" 
          alt="Foto KTP"
          class="mx-auto" 
          style="max-width: 100px; height: auto; border: 1px solid #ddd; margin-top: 5px;" 
        />
      </div>
      
      <!-- Gambar Kartu Keluarga -->
      <div class="flex flex-col items-center gap-2">
        <p class="font-bold text-slate-700">Foto KK</p>
        <img 
          src="${
            this.form.familyCardPhoto
              ? URL.createObjectURL(this.form.familyCardPhoto)
              : ""
          }" 
          alt="Foto Kartu Keluarga"
          class="mx-auto" 
          style="max-width: 100px; height: auto; border: 1px solid #ddd; margin-top: 5px;" 
        />
      </div>
    </div>
  `,
        showCancelButton: true,
        confirmButtonText: "Submit",
        cancelButtonText: "Edit",
      }).then((result) => {
        if (result.isConfirmed) {
          this.simulateSubmission();
        }
      });
    },
    simulateSubmission() {
      Swal.fire({
        title: "Submitting...",
        allowOutsideClick: false,
        didOpen: () => {
          Swal.showLoading();
        },
      });

      setTimeout(() => {
        const isSuccess = Math.random() > 0.5; // Simulate success or failure randomly

        if (isSuccess) {
          Swal.fire({
            title: "Success",
            text: "Form submitted successfully!",
            icon: "success",
            confirmButtonText: "OK",
          });
        } else {
          Swal.fire({
            title: "Error",
            text: "Submission failed, please try again.",
            icon: "error",
            confirmButtonText: "OK",
          });
        }
      }, 1500); // Simulate 1.5 seconds delay
    },
    async fetchProvinces() {
      try {
        const response = await axios.get(
          "https://emsifa.github.io/api-wilayah-indonesia/api/provinces.json"
        );
        this.provinces = response.data;
      } catch (error) {
        console.error("Failed to fetch provinces:", error);
      }
    },
    async fetchCities() {
      if (this.form.province !== "Other") {
        try {
          const provinceId = this.provinces.find(
            (prov) => prov.name === this.form.province
          )?.id;
          const response = await axios.get(
            `https://emsifa.github.io/api-wilayah-indonesia/api/regencies/${provinceId}.json`
          );
          this.cities = response.data;
        } catch (error) {
          console.error("Failed to fetch cities:", error);
        }
      } else {
        this.cities = [];
      }
    },
    async fetchSubDistricts() {
      if (this.form.city !== "Other") {
        try {
          const cityId = this.cities.find(
            (cit) => cit.name === this.form.city
          )?.id;
          const response = await axios.get(
            `https://emsifa.github.io/api-wilayah-indonesia/api/districts/${cityId}.json`
          );
          this.subDistricts = response.data;
        } catch (error) {
          console.error("Failed to fetch sub-districts:", error);
        }
      } else {
        this.subDistricts = [];
      }
    },
    async fetchVillages() {
      if (this.form.subDistrict !== "Other") {
        try {
          const subDistrictId = this.subDistricts.find(
            (sub) => sub.name === this.form.subDistrict
          )?.id;
          const response = await axios.get(
            `https://emsifa.github.io/api-wilayah-indonesia/api/villages/${subDistrictId}.json`
          );
          this.villages = response.data;
        } catch (error) {
          console.error("Failed to fetch villages:", error);
        }
      } else {
        this.villages = [];
      }
    },
  },
  mounted() {
    this.fetchProvinces();
  },
};
</script>

<style scoped>
/* Add custom styles if needed */
</style>
