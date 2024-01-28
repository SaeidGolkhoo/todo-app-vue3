<template>
  <button type="button" class="btn btn-info">Add</button>
  <table class="table table-dark table-striped text-center text-capitalize">
    <thead>
      <tr>
        <th>row</th>
        <th>task Name</th>
        <th>how Long</th>
        <th>status</th>
        <th>delete</th>
        <th>edit</th>
        <th>change status</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>1</td>
        <td>chart component</td>
        <td>3Days</td>
        <td>Active</td>
        <td><button type="button" class="btn btn-danger">Delete</button></td>
        <td><button type="button" class="btn btn-warning">Edit</button></td>
        <td>
          <button type="button" class="btn btn-success">Change Stat</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup></script>
