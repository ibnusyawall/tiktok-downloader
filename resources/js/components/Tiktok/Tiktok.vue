<template>
    <div>
            <br><br>
            <h2 class="text-center"> TikTok Downloader  </h2>
            <form v-on:submit.prevent="submitForm">
                <div class="form-group">
                    <label for="name">Enter Url</label>
                    <input type="text" class="form-control" id="url" placeholder="https://vt.tiktok.com/ZSJ6dbHte/" v-model="form.url">
                </div>
                <div class="form-group">
                    <label for="name">Result</label>
                    <input type="text" class="form-control" id="result" v-model="form.result" disabled>
                </div>
                <div class="form-group">
                    <button class="btn btn-primary">Submit</button>
                    <a class="btn btn-success" role="button" :href="link">Download</a>
                    <button type="button" class="btn btn-secondary" data-toggle="tooltip" data-placement="top" title="Copied!" @click="copyLink">Copy Link </button>
                </div>
                <div class="embed-responsive embed-responsive-16by9">
                    <iframe class="embed-responsive-item" :src="embed"></iframe>
                </div>
            </form>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                form: {
                    url: '',
                    result: ''
                },
                embed: '',
                link: '#'
            }
        },
        methods: {
            submitForm() {
                    axios.post('https://tiktokd.herokuapp.com/tiktok', { url: this.form.url })
                        .then(res => {
                            this.link = res.data.data.link
                            this.embed = res.data.data.link
                            this.form.result = res.data.data.link
                        })
                        .catch(e => {
                            this.form.result = e
                        })
            },
            copyLink() {
                if (!this.form.result) return
                this.$copyText(this.form.result)
                    .then( function(e) {
                       console.log(e)
                    }, function(e) {
                       console.log(e)  
                    })
            }
        }
    }
</script>
