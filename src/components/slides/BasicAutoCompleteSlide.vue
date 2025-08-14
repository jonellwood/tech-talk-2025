<template>
  <div class="slide fade-in">
    <h2>Basic Auto-Complete</h2>
    <h3>Level 1: Simple Integration</h3>

    <ul>
      <li>Customer name/email lookup that fills address, phone, account details</li>
      <li>Employee ID lookup for internal forms</li>
      <li>Simple to implement, reduce opportunities for errors</li>
      <li>Reduce to as close to a single source of truth as possible</li>
    </ul>

    <div class="highlight-box">
      <h3>Implementation Example</h3>
      <p>User types "john.d" → System suggests "john.doe@company.com" → Auto-fills: phone, department, manager, start date</p>
    </div>

    <div style="margin-top: 2rem;">
      <p><strong>Impact:</strong> 80% reduction in form completion time for returning customers</p>
    </div>
  </div>
</template>

<script setup>
// Speaker Notes:
// - This is the easiest win - start here
// - Most systems already have search capabilities
// - Focus on high-volume, repetitive forms first
// - Example should resonate with HR and customer service teams
// - Time: 2-3 minutes
</script>
