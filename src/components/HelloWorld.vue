<template>
  <div>
    <header>
      <MDBNavbar expand="lg" light bg="white" container>
        <MDBNavbarToggler></MDBNavbarToggler>
        <MDBNavbarNav collapse="navbarExample01" class="mb-2 mb-lg-0">
          <MDBNavbarItem to="#" active>
            Home
          </MDBNavbarItem>
          <MDBNavbarItem to="#">
            Features
          </MDBNavbarItem>
          <MDBNavbarItem to="#">
            Pricing
          </MDBNavbarItem>
          <MDBNavbarItem to="#">
            About
          </MDBNavbarItem>
        </MDBNavbarNav>
      </MDBNavbar>
      <!-- Jumbotron -->
      <div class="p-5 text-center bg-light">
        <h1 class="mb-3">Store Items</h1>
        <h4 class="mb-3">Subheading</h4>
        <a href="" class="btn btn-primary" role="button">
          Call-to-action
        </a>
      </div>
    </header>

    <div v-if="storeitems.length">
      <MDBRow :cols="['1','md-4']" class="g-4">
      <div v-for="item in storeitems" :key="item.id">
        <MDBCol>
          <MDBCard>
            <MDBCardImg :src="imageLink + item.Image.url" top alt="..."/>
            <MDBCardBody>
              <MDBCardTitle>
                {{ item.Title }}
              </MDBCardTitle>
              <MDBCardText>
                {{ item.Description }}
              </MDBCardText>
              <div>{{ item.Price }} €</div>
            </MDBCardBody>
          </MDBCard>
        </MDBCol>
      </div>
      </MDBRow>
    </div>
  </div>
</template>

<script>
  import { MDBNavbar, MDBNavbarToggler, MDBNavbarNav, MDBNavbarItem, MDBCol, MDBRow, MDBCard, MDBCardBody, MDBCardTitle, MDBCardText, MDBCardImg } from 'mdb-vue-ui-kit';
  export default {
  name: 'HelloWorld',
  components: {
    MDBNavbar,
    MDBNavbarToggler,
    MDBNavbarNav,
    MDBNavbarItem,
    MDBCol,
    MDBRow,
    MDBCard,
    MDBCardBody,
    MDBCardTitle,
    MDBCardText,
    MDBCardImg
  },
  data(){
    return {
      storeitems: [],
      imageLink: "http://localhost:1337"
    }
  },
  created() {
    fetch("http://localhost:1337/storeitems")
    .then((res) => res.json())
    .then((data) => {
      this.storeitems = data;
    });
  }
}
</script>

<script>

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
