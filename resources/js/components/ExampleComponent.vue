<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>

                    <div class="card-body">
                        I'm an example component.
                    </div>
                    <passport-clients></passport-clients>
                    <passport-authorized-clients></passport-authorized-clients>
                    <passport-personal-access-tokens></passport-personal-access-tokens>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Axios from "axios";

    export default {
        mounted() {
            console.log('Component mounted.')

            let channel = Echo.channel('user-channel')
            channel.listen('.UserEvent', function (data) {
                console.log(data);
            });

            Axios.get('/api/user').then(data => console.log(data)).catch(err => console.log(err))
        }
    }
</script>
