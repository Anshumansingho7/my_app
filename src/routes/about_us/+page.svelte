<script lang="ts">
  let fullName: string = '';
  let email: string = '';
  let dob: string = '';
  let position: string = 'developer';
  let gender: string = '';
  let terms: boolean = false;
  let resume: FileList | null = null;
  let submittedData: { 
    fullName: string; 
    email: string; 
    dob: string; 
    position: string; 
    gender: string; 
    terms: boolean; 
    resume: string; 
  } | null = null;

  function handleSubmit(event: Event): void {
    event.preventDefault();

    submittedData = {
      fullName,
      email,
      dob,
      position,
      gender,
      terms,
      resume: resume ? resume[0].name : 'No file uploaded' // Get the file name
    };
  }
</script>

<main>
  <h1>Job Application Form</h1>
  <form on:submit={handleSubmit}>
    <!-- Full Name -->
    <div class="form-group">
      <label for="fullName">Full Name:</label>
      <input type="text" id="fullName" bind:value={fullName} required />
    </div>

    <!-- Email -->
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" id="email" bind:value={email} required />
    </div>

    <!-- Date of Birth -->
    <div class="form-group">
      <label for="dob">Date of Birth:</label>
      <input type="date" id="dob" bind:value={dob} required />
    </div>

    <!-- Resume Upload -->
    <div class="form-group">
      <label for="resume">Upload Resume:</label>
      <input type="file" id="resume" bind:files={resume} accept=".pdf,.doc,.docx" required />
    </div>

    <!-- Job Position -->
    <div class="form-group">
      <label for="position">Job Position:</label>
      <select id="position" bind:value={position} required>
        <option value="developer">Developer</option>
        <option value="designer">Designer</option>
        <option value="manager">Manager</option>
      </select>
    </div>

    <!-- Gender -->
    <div class="form-group">
      <label for="gender">Gender:</label>
      <div class="radio-group">
        <input type="radio" id="male" name="gender" value="male" bind:group={gender} required />
        <label for="male">Male</label>
        <input type="radio" id="female" name="gender" value="female" bind:group={gender} />
        <label for="female">Female</label>
      </div>
    </div>
    
    <!-- Terms and Conditions -->
    <div class="form-group checkbox-group">
      <input type="checkbox" id="terms" bind:checked={terms} required />
      <label for="terms">I agree to the terms and conditions</label>
    </div>

    <!-- Submit Button -->
    <button type="submit">Submit Application</button>
  </form>

  <!-- Display Submitted Data -->
  {#if submittedData}
    <div class="submitted-data">
      <h2>Submitted Data</h2>
      <p><strong>Full Name:</strong> {submittedData.fullName}</p>
      <p><strong>Email:</strong> {submittedData.email}</p>
      <p><strong>Date of Birth:</strong> {submittedData.dob}</p>
      <p><strong>Job Position:</strong> {submittedData.position}</p>
      <p><strong>Gender:</strong> {submittedData.gender}</p>
      <p><strong>Terms Accepted:</strong> {submittedData.terms ? 'Yes' : 'No'}</p>
      <p><strong>Resume:</strong> {submittedData.resume}</p>
    </div>
  {/if}
</main>

<style>
  main {
    text-align: center;
    padding: 2em;
    max-width: 600px;
    margin: 2em auto;
    background-color: #f4f4f9;
    border-radius: 12px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    font-family: 'Arial', sans-serif;
  }
  
  h1 {
    color: #333;
    margin-bottom: 1.5em;
    font-size: 2em;
    font-weight: 700;
  }
  
  .form-group {
    margin-bottom: 1.5em;
    text-align: left;
  }
  
  label {
    font-weight: bold;
    color: #555;
    margin-bottom: 0.5em;
    display: inline-block;
  }
  
  input[type="text"],
  input[type="email"],
  input[type="date"],
  select,
  input[type="file"] {
    width: 100%;
    padding: 0.75em;
    margin-top: 0.5em;
    border: 2px solid #ccc;
    border-radius: 8px;
    font-size: 1em;
    color: #333;
    background-color: #fff;
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.05);
    transition: border-color 0.3s ease;
  }
  
  input:focus,
  select:focus {
    border-color: #007bff;
    outline: none;
  }
  
  .radio-group {
    display: flex;
    gap: 1.5em;
  }
  
  .checkbox-group {
    display: flex;
    align-items: center;
    gap: 0.5em;
    margin-top: 1em;
  }
  
  button {
    background-color: #007bff;
    color: white;
    padding: 0.75em 2em;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    margin-top: 1.5em;
    font-size: 1.1em;
    font-weight: bold;
    box-shadow: 0 4px 10px rgba(0, 123, 255, 0.4);
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
  }
  
  button:hover {
    background-color: #0056b3;
    box-shadow: 0 6px 15px rgba(0, 123, 255, 0.6);
  }
  
  .submitted-data {
    margin-top: 2em;
    text-align: left;
    background-color: #fff;
    padding: 1.5em;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    font-size: 1em;
    color: #555;
  }
  
  .submitted-data h2 {
    color: #333;
    margin-bottom: 1em;
    font-size: 1.5em;
    font-weight: 700;
  }
  
  .submitted-data p {
    margin: 0.5em 0;
    color: #666;
  }
</style>
  