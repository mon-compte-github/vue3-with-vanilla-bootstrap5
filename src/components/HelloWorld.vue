<template>

<div class="card">
  <div class="card-body">

    <h1>{{ msg }}</h1>

    <div class="alert alert-secondary alert-dismissible fade show" role="alert">
      <strong>Hey!</strong> This is a bootstrap5 powered app \0/
      <button type="button" class="close" data-dismiss="alert" aria-label="Close">
        <span aria-hidden="true">&times;</span>
      </button>
    </div>

    <h2>Buttons</h2>
    <div>
      <button type="button" class="btn btn-primary mr-1">Primary</button>
      <button type="button" class="btn btn-secondary mr-1">Secondary</button>
      <button type="button" class="btn btn-success">Success</button>
    </div>

    <h2>Forms</h2>
    <form>
      <!-- form-group no longer exists ... -->
      <div class="form-group">
        <label for="exampleInputEmail1">Email address</label>
        <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
      </div>
      <div class="form-group">
        <label for="exampleInputPassword1">Password</label>
        <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
      </div>
      <div class="form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1">
        <label class="form-check-label" for="exampleCheck1">Check me out</label>
      </div>
      <select class="form-control form-control-lg">
        <option>Large select</option>
      </select>
      <button type="submit" class="btn btn-primary mt-1">Submit</button>
    </form>

    <!--form class="form-inline"-->
    <form class="d-flex mt-5" style="flex-direction: row; align-items: center">
      <label class="sr-only" for="inlineFormInputName2">Name</label>
      <input type="text" class="form-control mb-2 mr-sm-2" id="inlineFormInputName2" placeholder="Jane Doe">

      <label class="sr-only" for="inlineFormInputGroupUsername2">Username</label>
      <div class="input-group mb-2 mr-sm-2">
        <div class="input-group-prepend">
          <div class="input-group-text">@</div>
        </div>
        <input type="text" class="form-control" id="inlineFormInputGroupUsername2" placeholder="Username">
      </div>

      <div class="form-check mb-2 mr-sm-2">
        <input class="form-check-input" type="checkbox" id="inlineFormCheck">
        <label class="form-check-label" for="inlineFormCheck">
          Remember me
        </label>
      </div>

      <button type="submit" class="btn btn-primary mb-2">Submit</button>
    </form>

    <h2>Dropdowns</h2>
    <div class="btn-group">
      <button type="button" class="btn btn-info dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        Action
      </button>
      <div class="dropdown-menu">
        <a class="dropdown-item" href="#">Action</a>
        <a class="dropdown-item" href="#">Another action</a>
        <a class="dropdown-item" href="#">Something else here</a>
        <div class="dropdown-divider"></div>
        <a class="dropdown-item" href="#">Separated link</a>
      </div>
    </div>

    <h2>Modals</h2>
    <div>
      <button type="button" class="btn btn-primary mr-1" data-toggle="modal" data-target="#exampleModal">Attribute</button>
      <button type="button" class="btn btn-dark" @click="showModal()">Javascript</button>
    </div>


    <h2>Breadcrumb</h2>
    <span>This component won't be displayed properly since corresponding style has been commented out in <code>custom.scss</code></span>
    <nav aria-label="breadcrumb">
      <ol class="breadcrumb">
        <li class="breadcrumb-item active" aria-current="page">Home</li>
      </ol>
    </nav>

    <h2>Popovers</h2>
    <div>
      <button ref="popoverRef" id="pop-pop-pop" type="button" class="btn btn-dark" @click="showPopover()">Javascript</button>
    </div>

  </div>

  <div id="exampleModal" ref="modalRef" class="modal" tabindex="-1" role="dialog">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Modal title</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <p>Modal body text goes here.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-primary">Save changes</button>
          <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>

</div>

</template>

<script>

import { onMounted, ref } from 'vue'
import { Popover, Modal } from 'bootstrap'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup() {

    // will be assigned when component is attached to DOM
    // don't forget to "export" these variables 
    // (see the final return statement below)
    // or they will remain null ...
		const popoverRef = ref(null);
    const modalRef = ref(null);
    
    const showModal = () => {
      const dialog = new Modal(modalRef.value, { backdrop: true });
      dialog.show();
    };

    const showPopover = () => {
      const popover = new Popover(popoverRef.value, { content: 'Hello world!', placement: 'top' });
      popover.show();
    };

    onMounted(() => {
      /*
      // vanilla style, also working :)
      const el = document.getElementById('pop-pop-pop');
      const popover = new Popover(el, { content: 'Hello world!', placement: 'top' });
      el.addEventListener('click', () => {
        popover.show();
      }, false);
      */
    });

    return { modalRef, popoverRef, showModal, showPopover }
  }
}
</script>

<style lang="scss" scoped>

@import "../../node_modules/bootstrap/scss/functions";
@import "../../node_modules/bootstrap/scss/variables";
@import "../../node_modules/bootstrap/scss/mixins";

// additional styling, scoped to this component
button.close {
  background-color: transparent;;
  border: 0;
}

h2 {
  margin-top: 1em;
  margin-bottom: 1em;
}

// responsiveness example

// default size, apply to small devices
div.card {
  margin: 2em auto 2em auto;
  width: 90vw;
}

@include media-breakpoint-up(md) {
  div.card {
    width: 80vw;
  }
}

@include media-breakpoint-up(lg) {
  div.card {
    width: 70vw;
  }
}

@include media-breakpoint-up(lg) {
  div.card {
    width: 50vw;
  }
}

</style>
