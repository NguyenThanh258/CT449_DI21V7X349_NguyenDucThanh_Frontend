<template>
    <div class="page">
        <h4>Thêm mới Liên hệ</h4>
        <ContactForm :contact="newContact" @onSubmit="addContact" />
        <p>{{ message }}</p>
    </div>
</template>

<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";
    export default {
        components: {ContactForm,
        },
        data() {
            return {
                message: "",
                newContact: {}                
            };
        },
        methods: {
            async addContact(data) {
                try {
                    await ContactService.create(data);
                    alert('Liên hệ được thêm mới thành công.');
                    this.$router.push({ name: "contactbook" });
                } catch (error) {
                    console.log(error);
                }
            },
        },
    };
</script>