<template>
  <div class="container-fluid p-0" id="page">
    <img
      src="../assets/png/header.png"
      alt="header"
      style="width: auto; max-height: 200px; margin-top: 10px"
      id="header"
    />

    <h1
      class="align-self-center font-weight-bold"
      style="
        margin-top: 10px;
        color: white;
        font-family: Space Grotesk;
        border-bottom: 2px solid white;
        padding-bottom: 25px;
        margin-bottom: 50px;
        font-size: 60px;
      "
    >
      Puntara's Portfolio
    </h1>

    <h1
      id="project-title"
      class="align-self-center p-2 font-weight-bold"
      style="
        font-family: Space Grotesk;
        color: #febea1;

        margin-bottom: 25px;
      "
    >
      <span
        class="px-5 py-2 shadow-box"
        style="background-color: white; border-radius: 25px"
        >Projects</span
      >
    </h1>

    <div
      class="container p-4 shadow-box"
      style="background-color: white; border-radius: 50px; max-width: 1000px"
    >
      <!-- --------------------Projects -------------------------------------------------------------------- -->
      <div id="project-content" class="container-fluid box">
        <!-- -------------------------------timeline------------------------------------------------------------------------ -->
        <div class="container">
          <div
            class="row project-set m-4 p-4"
            style="border-radius: 25px"
            v-for="project in allProject"
            v-bind:name="project.title"
            v-on:click="showDetail(project)"
            data-toggle="modal"
            data-target="#detailModal"
          >
            <!-- begin timeline-time  (Left)-->
            <div class="col-1 text-right">
              <h5 class="date font-weight-bold">{{ project.date }}</h5>
            </div>

            <div class="col-11">
              <div class="container-fluid row">
                <div class="col-6">
                  <img
                    class="project-icon"
                    style="border-radius: 50%; width: 50%; min-width: 80px"
                    v-bind:src="project.img_title"
                    alt="icon"
                  />
                </div>
                <div class="col-6 text-left d-flex align-items-center">
                  <h2 class="font-weight-bold project-title">{{ project.title }}</h2>
                </div>
              </div>
            </div>

            <div class="container mt-4 border-top pt-4 sub-detail">
              <h6>{{ project.sub }}</h6>
            </div>
            <!-- end row of project -->
          </div>

          <!-- ------End-timeline------ -->
        </div>
      </div>
    </div>
    <img
      src="../assets/png/profile.png"
      alt="profile"
      style="
        border-radius: 50%;
        width: 40vh;

        margin-top: 100px;
        border: 10px solid white;
      "
    />
    <div
      class="container p-4 shadow-box"
      style="
        background-color: white;
        border-radius: 50px;
        margin-top: -150px;
        max-width: 1000px;
      "
    >
      <!-- ----------------------- About ------------------------------------ -->
      <div id="about-content" class="container-fluid box" style="padding-top: 150px">
        <h1 class="align-self-center m-1" style="">Puntara Arunratanadilok</h1>
        <h3 class="align-self-center m-1" style="">
          <i class="fa-solid fa-envelope"></i>
          &nbsp; puntara.arun@gmail.com
        </h3>
      </div>
    </div>

    <img src="../assets/png/footer.png" alt="footer" style="width: 100%; bottom: 0rem" />

    <!-- ------------------------ Button Set ---------------------------------- -->
    <button class="back-to-top btn btn-light" @click="backTop()">
      <i class="fa-solid fa-angle-up"></i>
    </button>
    <button
      class="navigate-btn btn btn-light dropdown show"
      id="dropdownMenuLink"
      data-toggle="dropdown"
      aria-haspopup="true"
      aria-expanded="false"
    >
      <i class="fa-solid fa-bars"></i>
    </button>
    <div
      class="dropdown-menu"
      aria-labelledby="dropdownMenuLink"
      style="border-radius: 25px"
    >
      <button class="dropdown-item" @click="navigateTo('project-title')">
        <i class="fa-solid fa-folder"></i>&nbsp;&nbsp;Projects
      </button>

      <button class="dropdown-item" @click="navigateTo('about-content')">
        <i class="fa-solid fa-user"></i>&nbsp;&nbsp;Author
      </button>
    </div>

    <!-- --------------------------------- Modal ----------------------------------------------------- -->

    <!-- Modal -->
    <div
      class="modal fade"
      id="detailModal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="detailModal"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-dialog-centered modal-xl" role="document">
        <div style="height: 80%; border-radius: 25px" class="modal-content">
          <div
            class="modal-header"
            style="background: rgba(255, 191, 161, 1); border-radius: 25px 25px 0px 0px"
          >
            <h1
              class="modal-title font-weight-bold p-2"
              style="font-family: Space Grotesk"
              id="modal_title"
            ></h1>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div class="container-fluid border-bottom row m-0 py-3">
              <div class="col-lg-6">
                <img
                  id="modal_img"
                  class="img-fluid"
                  src="../assets/png/tempprofile.png"
                  alt=""
                  style="border-radius: 20px; border: 5px solid #febfa2"
                />
              </div>
              <div class="col-lg-6 text-left pt-3">
                <h5 class="font-weight-bold pb-2">
                  <span class="headline-detail">Description</span>
                </h5>
                <p id="modal_description"></p>
              </div>
            </div>

            <div class="text-left">
              <div class="row border-bottom py-4 px-4">
                <div class="col-lg-4 border-right pl-4 pt-4">
                  <h5 class="font-weight-bold pb-2">
                    <span class="headline-detail">Feature</span>
                  </h5>

                  <li id="modal_os"></li>
                  <li id="modal_language"></li>
                  <li id="modal_software"></li>
                  <li id="modal_genre"></li>
                  <li id="modal_contributed"></li>
                  <li id="modal_course"></li>
                </div>

                <div class="col-lg-8 pt-4">
                  <h5 class="font-weight-bold pb-2">
                    <span class="headline-detail">My Responsibility</span>
                  </h5>
                  <div id="modal_responsibility"></div>
                </div>
              </div>

              <h5 class="font-weight-bold p-4">
                <span class="headline-detail">Gallery</span>
              </h5>
              <!-- -------------- Gallery --------------------- -->
              <div
                id="carouselExampleIndicators"
                class="carousel slide px-4"
                data-ride="carousel"
              >
                <ol id="photo_indicators" class="carousel-indicators"></ol>
                <div
                  id="photo_carousel"
                  class="carousel-inner"
                  style="border-radius: 20px"
                ></div>
                <a
                  class="carousel-control-prev"
                  href="#carouselExampleIndicators"
                  role="button"
                  data-slide="prev"
                >
                  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                  <span class="sr-only">Previous</span>
                </a>
                <a
                  class="carousel-control-next"
                  href="#carouselExampleIndicators"
                  role="button"
                  data-slide="next"
                >
                  <span class="carousel-control-next-icon" aria-hidden="true"></span>
                  <span class="sr-only">Next</span>
                </a>
              </div>

              <!-- -------------End Gallery ------------------- -->
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">
              Close
            </button>
            <button
              id="modal_link"
              type="button"
              class="btn btn-dark"
              style="background-color: #6e5494"
            >
              <i class="fa fa-github"></i>&nbsp; Github
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- --------------------------------- End Modal ----------------------------------------------------- -->
</template>

<script>
import project_json from "../assets/content/projectlist.json";
export default {
  name: "Home",
  data() {
    return {
      allProject: project_json.projects,
    };
  },

  methods: {
    setGallery(myGallery) {
      for (let i = 0; i < myGallery.length; i++) {
        if (i == 0) {
          $("#photo_indicators").html("");
          $("#photo_carousel").html("");

          $("#photo_indicators").append(
            '<li data-target="#carouselExampleIndicators" data-slide-to="' +
              i +
              '" class="active" ></li>'
          );
          $("#photo_carousel").append(
            '<div class="carousel-item active" id="' +
              "gallery" +
              i +
              '"> <img class="d-block w-100"  src="' +
              myGallery[i].link +
              '" />'
          );
        } else {
          $("#photo_indicators").append(
            '<li data-target="#carouselExampleIndicators" data-slide-to="' + i + '"></li>'
          );
          $("#photo_carousel").append(
            '<div class="carousel-item" id="' +
              "gallery" +
              i +
              '"> <img class="d-block w-100" src="' +
              myGallery[i].link +
              '" />'
          );
        }
        $("#gallery" + i).append(
          '<div class="carousel-caption d-none d-md-block" style="background-color: rgb(0, 0, 0,30%);"> <h5>' +
            myGallery[i].topic +
            "</h5>  <p> " +
            myGallery[i].descript +
            "</p>  </div></div>"
        );
      }
    },

    showDetail(project) {
      $("#modal_title").text(project.title);
      $("#modal_img").attr("src", project.img_detail);

      $("#modal_os").html("<b>Operating System :</b> " + project.os);
      $("#modal_language").html("<b>Programming Languages :</b> " + project.language);
      $("#modal_software").html("<b>Software :</b> " + project.software);
      $("#modal_genre").html("<b>Genre :</b> " + project.genre);
      $("#modal_contributed").html("<b>Contributed by :</b> " + project.contributed);
      $("#modal_course").html("<b>Course :</b> " + project.course);

      $("#modal_description").text(project.description);
      $("#modal_responsibility").html("");
      $.each(project.responsibility, function (index, item) {
        $("#modal_responsibility").append("<li>" + item + "</li>");
      });
      if (project.github) {
        $("#modal_link").show();
        $("#modal_link").attr(
          "onclick",
          "window.open('" + project.github + "','_blank')"
        );
      } else {
        $("#modal_link").hide();
      }

      this.setGallery(project.gallery);
    },

    backTop() {
      document.body.scrollIntoView({
        behavior: "smooth",
      });
    },

    navigateTo(content_id) {
      $("#" + content_id)[0].scrollIntoView({
        behavior: "smooth",
      });
    },
  },
};
</script>
