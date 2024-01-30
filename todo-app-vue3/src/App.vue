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
    <!-- TouristsList.vue -->
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
          <td>
            <span class="badge bg-success" v-if="item.status === true"
              >Active</span
            >
            <span class="badge bg-danger" v-else>Inactive</span>
          </td>
          <td>
            <button
              @click="deleteRow(index)"
              type="button"
              class="btn btn-danger rounded-pill"
            >
              Delete
            </button>
          </td>
          <td>
            <button
              type="button"
              class="btn btn-warning rounded-pill"
              data-bs-toggle="modal"
              data-bs-target="#editModal"
              @click="editTodo(index)"
            >
              Edit
            </button>
          </td>
          <td>
            <button
              @click="changeStatus(item)"
              type="button"
              class="btn btn-success rounded-pill"
            >
              Change Status
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <!--ModalBs.vue-->
    <!--AddForm-->
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
              ref="btnModalAddClose"
            ></button>
          </div>

          <!-- Modal body -->
          <div class="modal-body">
            <div
              v-if="showErrorForm === true"
              class="alert alert-danger text-center"
            >
              Please fill the form.
            </div>
            <input
              type="text"
              class="form-control mt-3 rounded-pill"
              placeholder="Task Name"
              v-model="taskName"
            />
            <input
              type="text"
              class="form-control mt-3 rounded-pill"
              placeholder="How Long"
              v-model="howLong"
            />
            <div class="d-grid">
              <button
                @click="addTodoList()"
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

    <!--ModalBs.vue-->
    <!--EditForm.vue-->
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
              v-model="editTaskName"
            />
            <input
              type="text"
              class="form-control mt-3 rounded-pill"
              placeholder="How Long"
              v-model="editHowLong"
            />
            <div class="d-grid">
              <button
                type="button"
                class="btn btn-block btn-success mt-3 rounded-pill"
                @click="editArray()"
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
import { reactive, ref } from "vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";

const taskName = ref("");
const howLong = ref("");
const showErrorForm = ref(false);

const editTaskName = ref("");
const editHowLong = ref("");
const indexArray = ref(0);

const btnModalAddClose = ref(null);

const todoList = reactive([
  { taskName: "a", howLong: "2weeks", status: true },
  { taskName: "b", howLong: "3weeks", status: false },
  { taskName: "c", howLong: "4weeks", status: false },
  { taskName: "d", howLong: "5weeks", status: true },
  { taskName: "e", howLong: "6weeks", status: false },
]);

function editTodo(index) {
  editTaskName.value = todoList[index].taskName;
  editHowLong.value = todoList[index].howLong;
  indexArray.value = index;
}

function editArray() {
  todoList[indexArray.value].taskName = editTaskName.value;
  todoList[indexArray.value].howLong = editHowLong.value;
}

function changeStatus(item) {
  if (confirm("Are you sure to change the status!") == true) {
    item.status = !item.status;

    toast("Good, it done", {
      type: "success",
      position: "top-center",
      transition: "flip",
      dangerouslyHTMLString: true,
    });
  }
}
function deleteRow(index) {
  if (confirm("Are you sure to delete!") == true) {
    todoList.splice(index, 1);
    toast("Good, it deleted!", {
      type: "success",
      position: "top-center",
      transition: "flip",
      dangerouslyHTMLString: true,
    });
  }
}
function addTodoList() {
  if (taskName.value != "" && howLong.value != "") {
    showErrorForm.value = false;

    todoList.push({
      taskName: taskName.value,
      howLong: howLong.value,
      status: true,
    });

    btnModalAddClose.value.click();
    taskName.value = "";
    howLong.value = "";
  } else showErrorForm.value = true;
}
</script>
