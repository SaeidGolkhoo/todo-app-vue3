<template>
  <button
    type="button"
    class="btn btn-info"
    data-bs-toggle="modal"
    data-bs-target="#addModal"
  >
    Add
  </button>
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

  <!-- The Modal -->
  <div class="modal fade" id="addModal">
    <div class="modal-dialog">
      <div class="modal-content">
        <!-- Modal Header -->
        <div class="modal-header">
          <h4 class="modal-title">Add Todo</h4>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
          ></button>
        </div>

        <!-- Modal body -->
        <div class="modal-body">
          <input
            type="text"
            class="form-control mt-3"
            placeholder="Task Name"
          />
          <input type="text" class="form-control mt-3" placeholder="How Long" />
          <div class="d-grid">
            <button type="button" class="btn btn-block btn-success mt-3">
              Add Todo
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup></script>
