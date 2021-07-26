<template>
  <div class="container">
    <div class="view-account">
      <section class="module">
        <div class="module-inner">
          <div class="side-bar">
            <div class="user-info">
              <img
                class="img-profile img-circle img-responsive center-block"
                src="https://bootdey.com/img/Content/avatar/avatar6.png"
                alt
              />
              <ul class="meta list list-unstyled">
                <li class="name">
                  {{ user.username }}
                  <label class="label label-info">Secretary</label>
                </li>
                <li class="email">
                  <a href="#">myemail.S@website.com</a>
                </li>
                <li class="activity">Last logged in: Today at 2:18pm</li>
              </ul>
            </div>
            <nav class="side-menu">
              <ul class="nav">
                <li>
                  <a href="#">
                    <span class="fa fa-user"></span> Profile
                  </a>
                </li>
                <li>
                  <a href="#">
                    <span class="fa fa-cog"></span> Settings
                  </a>
                </li>
                <li class="active">
                  <a href="#">
                    <span class="fa fa-credit-card"></span> Billing
                  </a>
                </li>
                <li>
                  <a href="#">
                    <span class="fa fa-envelope"></span> Messages
                  </a>
                </li>

                <li>
                  <a href="user-drive.html">
                    <span class="fa fa-th"></span> Drive
                  </a>
                </li>
                <li>
                  <a href="#">
                    <span class="fa fa-clock-o"></span> Reminders
                  </a>
                </li>
              </ul>
            </nav>
          </div>

          <div class="content-panel">
            <div class="content-header-wrapper">
              <h2 class="title">My Drive</h2>
            </div>
            <div class="content-utilities">
              <div class="page-nav">
                <span class="indicator">View:</span>
                <div class="btn-group" role="group">
                  <button
                    class="active btn btn-default"
                    data-toggle="tooltip"
                    data-placement="bottom"
                    title
                    data-original-title="Grid View"
                    id="drive-grid-toggle"
                  >
                    <i class="fa fa-th-large"></i>
                  </button>
                  <button
                    class="btn btn-default"
                    data-toggle="tooltip"
                    data-placement="bottom"
                    title
                    data-original-title="List View"
                    id="drive-list-toggle"
                  >
                    <i class="fa fa-list-ul"></i>
                  </button>
                </div>
              </div>
              <div class="actions">
                <div class="btn-group">
                  <button
                    class="btn btn-default dropdown-toggle"
                    data-toggle="dropdown"
                    type="button"
                    aria-expanded="false"
                  >
                    All Items
                    <span class="caret"></span>
                  </button>
                  <ul class="dropdown-menu">
                    <li>
                      <a href="#">
                        <i class="fa fa-file"></i> Documents
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-file-image-o"></i> Images
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-file-video-o"></i> Media Files
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-folder"></i> Folders
                      </a>
                    </li>
                  </ul>
                </div>
                <div class="btn-group">
                  <button
                    class="btn btn-default dropdown-toggle"
                    data-toggle="dropdown"
                    type="button"
                    aria-expanded="false"
                  >
                    <i class="fa fa-filter"></i> Sorting
                    <span class="caret"></span>
                  </button>
                  <ul class="dropdown-menu">
                    <li>
                      <a href="#">Newest first</a>
                    </li>
                    <li>
                      <a href="#">Oldest first</a>
                    </li>
                  </ul>
                </div>
                <div class="btn-group" role="group">
                  <button
                    type="button"
                    class="btn btn-default"
                    data-toggle="tooltip"
                    data-placement="bottom"
                    title
                    data-original-title="Refresh"
                  >
                    <i class="fa fa-refresh"></i>
                  </button>
                  <button
                    type="button"
                    class="btn btn-default"
                    data-toggle="tooltip"
                    data-placement="bottom"
                    title
                    data-original-title="Archive"
                  >
                    <i class="fa fa-archive"></i>
                  </button>

                  <button
                    type="button"
                    class="btn btn-default"
                    data-toggle="tooltip"
                    data-placement="bottom"
                    title
                    data-original-title="Report spam"
                  >
                    <i class="fa fa-exclamation-triangle"></i>
                  </button>
                  <button
                    type="button"
                    class="btn btn-default"
                    data-toggle="tooltip"
                    data-placement="bottom"
                    title
                    data-original-title="Delete"
                  >
                    <i class="fa fa-trash-o"></i>
                  </button>
                </div>
              </div>
            </div>

            <div >
              <div class="row" v-if="!success">
                <div class="col-md-offset-5">
                  <p>Charger le fichier à signer</p>
                <input
                 v-if="!success"
                 id="files"
                 type="file"
                 @change="handleFileChange"
                />
              </div>
              </div>
              <br/> <br/>
              <div class="row" v-if="!success">
                <div class="col-md-offset-5">
                  <p>Charger votre clé privée</p>
                <input
                 v-if="!success"
                 id="files"
                 type="file"
                 @change="handlePrivateKeyChange"
                />
              </div>
              </div>
                <p class="text-success text-center" v-if="success">
                  <i class="fa fa-check fa-5x" aria-hidden="true"></i>
                  <br>
                  File Uploaded successfuly!
                </p>
              <br><br>
              <div class="text-center">
                Envoyer à:
               <select v-model="selectedUser">
                 <option value="user1">user1</option>
                 <option value="user2">user2</option>
                 <option value="user3">user3</option>
                 <option value="user4">user3</option>
               </select>
              </div> <br><br>
              <div class="text-center">
               <button class="btn btn-success" :disabled="!file" @click="upload">
                  SIGNER ET ENVOYER
                </button>
              </div>



            </div>

          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { mapGetters } from 'vuex';

export default {
  name: 'ComUpload',
  data() {
    return {
      file: null,
      privateKeyFile: null,
      success: false,
      API_HOST: 'http://127.0.0.1:3000',
      selectedUser:''
    };
  },
  computed: {
    ...mapGetters({
      user: 'auth/user',
    })
  },

  methods: {
    handleFileChange(e) {
      const files = e.target.files || e.dataTransfer.files;
      if (!files.length) {
        return true;
      }
      this.file = files[0];
      return true;
    },

    handlePrivateKeyChange(e) {
      const files = e.target.files || e.dataTransfer.files;
      if (!files.length) {
        return true;
      }
      this.privateKeyFile = files[0];
      return true;
    },


    upload() {
      const fileFormData = new FormData();
      const privateKeyFormData = new FormData();
      fileFormData.append('file', this.file);
      privateKeyFormData.append('file', this.privateKeyFile);
      axios.post(
          `${this.API_HOST}/api/containers/uploaded-pdf/upload?type=pdf&filename=${this.file.name}`,
          fileFormData,
          {
            headers: {
              'Content-Type': 'multipart/form-data'
            }
          }
      ).then(()=>{

       axios.post(
          `${this.API_HOST}/api/containers/uploaded-keys/upload?type=p12&filename=${this.privateKeyFile.name}`,
          privateKeyFormData,
          {
            headers: {
              'Content-Type': 'multipart/form-data'
            }
          }
      ).then(()=> {
          axios.get(`${this.API_HOST}/add-stamp?filename=${this.file.name}`)
          .then(({data})=> {
            if(data.result) {
                this.success = true;
               window.location=`${this.API_HOST}/sign?filename=${this.file.name}&privateKeyFilename=${this.privateKeyFile.name}`;
            } else {

            }
          });

          });

        });
    }


  }
};
</script>
