<template>
  <div class="container py-5">
    <button
      type="button"
      class="btn btn-info mb-2 rounded-pill px-5"
      data-bs-toggle="modal"
      data-bs-target="#addModal"
    >
      Add Todo
    </button>
    <table class="table table-dark table-striped text-center text-capitalize">
      <thead>
        <tr>
          <th><i class="bi bi-123"></i> row</th>
          <th><i class="bi bi-code-slash"></i> task Name</th>
          <th><i class="bi bi-alarm"></i> how Long</th>
          <th><i class="bi bi-lightbulb"></i> status</th>
          <th><i class="bi bi-trash"></i> delete</th>
          <th><i class="bi bi-pen"></i> edit</th>
          <th><i class="bi bi-lightbulb"></i> change status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in todoList">
          <td>{{ index + 1 }}</td>
          <td>{{ item.taskName }}</td>
          <td>{{ item.howLong }}</td>
          <td>{{ item.status }}</td>
          <td>
            <button type="button" class="btn btn-danger rounded-pill">
              Delete
            </button>
          </td>
          <td>
            <button
              type="button"
              class="btn btn-warning rounded-pill"
              data-bs-toggle="modal"
              data-bs-target="#editModal"
            >
              Edit
            </button>
          </td>
          <td>
            <button type="button" class="btn btn-success rounded-pill">
              Change Status
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <!-- The Add Modal -->
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
              class="form-control mt-3 rounded-pill"
              placeholder="Task Name"
            />
            <input
              type="text"
              class="form-control mt-3 rounded-pill"
              placeholder="How Long"
            />
            <div class="d-grid">
              <button
                type="button"
                class="btn btn-block btn-success mt-3 rounded-pill"
              >
                Add Todo
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- The Edit Modal -->
    <div class="modal fade" id="editModal">
      <div class="modal-dialog">
        <div class="modal-content">
          <!-- Modal Header -->
          <div class="modal-header">
            <h4 class="modal-title">Edit Todo</h4>
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
              class="form-control mt-3 rounded-pill"
              placeholder="Task Name"
            />
            <input
              type="text"
              class="form-control mt-3 rounded-pill"
              placeholder="How Long"
            />
            <div class="d-grid">
              <button
                type="button"
                class="btn btn-block btn-success mt-3 rounded-pill"
              >
                Edit Todo
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const todoList = [
  { taskName: "a", howLong: "2weeks", status: false },
  { taskName: "b", howLong: "3weeks", status: false },
  { taskName: "c", howLong: "4weeks", status: false },
  { taskName: "d", howLong: "5weeks", status: false },
  { taskName: "e", howLong: "6weeks", status: false },
];
</script>
