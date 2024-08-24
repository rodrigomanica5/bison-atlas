<template>
    <q-layout view="lHh Lpr lFf">
        <q-header style="background-color: #FFFFFF;" elevated>
            <q-toolbar>
                <q-toolbar-title>
                    <img class="q-mt-sm" src="/svg/BACPNG.png" alt="Bison Atlas Consulting" style="height: 70px;">
                </q-toolbar-title>
                <q-btn style="color: #08529d; font-weight: 900;" flat label="Home" @click="scrollTo('home')"></q-btn>
                <q-btn style="color: #08529d; font-weight: 900;" flat label="Why Choose Us"
                    @click="scrollTo('why-choose-us')"></q-btn>
                <q-btn style="color: #08529d; font-weight: 900;" flat label="Services"
                    @click="scrollTo('our-services')"></q-btn>
                <q-btn style="color: #08529d; font-weight: 900;" flat label="Contact"
                    @click="scrollTo('contact')"></q-btn>
            </q-toolbar>
        </q-header>

        <q-page-container style="background-color: #080C1E;">
            <q-page style="padding: 0px 100px;">

                <!-- Hero Section -->
                <div id="home" class="heroContainer q-mb-xl text-center text-white q-pa-xl">
                    <h1 style="font-weight: 900;">Bison Atlas Consulting</h1>
                    <h3 class="heroSubtitle">Your Remote Business Partner</h3>
                </div>

                <!-- Welcome Section -->
                <q-card style="border-radius: 50px;" class="q-mb-xl sectionContainer">
                    <q-card-section style="background-color: #FFFFFF;">
                        <h2 class="sectionTitle">Welcome</h2>
                        <p class="sectionDetail">
                            In today's fast-paced world, partnering with a trusted advisor who offers comprehensive
                            financial consulting and administrative support is crucial for achieving your business
                            and personal goals. At Bison Atlas Consulting, we leverage over a decade of professional
                            experience to provide top-notch services tailored to your needs.
                        </p>
                    </q-card-section>
                </q-card>

                <!-- Why Choose Us Section -->
                <q-card style="border-radius: 50px;" id="why-choose-us" class="q-mb-xl sectionContainer">
                    <q-card-section style="background-color: #FFFFFF;">
                        <h2 class="sectionTitle">Why Choose Us?</h2>
                        <p class="sectionDetail">
                            At Bison Atlas Consulting, we understand the challenges that come with managing finances
                            and administrative tasks. Our services are designed to support you in navigating these
                            complexities with ease. As a remote-first firm, we offer flexible, virtual solutions
                            that fit seamlessly into your schedule and business model. Whether you're looking for
                            meticulous bookkeeping, insightful financial advice, or reliable administrative support,
                            we are here to help.
                        </p>
                    </q-card-section>
                </q-card>

                <!-- Our Services Section -->
                <div style="border-radius: 50px; background-color: #FFFFFF;" id="our-services"
                    class="q-mb-xl sectionContainer">
                    <h2 style="margin-bottom: 0;" class="sectionTitle">Services</h2>
                    <q-page-container>
                        <q-row
                            style="display: flex; flex-direction: row; flex-wrap: wrap; justify-content: space-around;"
                            class="q-col-gutter-md q-justify-around">
                            <template v-for="(element, index) in services" :key="index">
                                <q-card style="width: 30%; margin-bottom: 20px;" class="q-mx-sm">
                                    <q-card-section>
                                        <h3 class="serviceTitle" style="text-align: right; margin-top: 0;">{{ element.id
                                            }}</h3>
                                        <h5 class="serviceTitle">{{ element.name }}</h5>
                                        <p class="serviceDetail">{{ element.description }}</p>
                                    </q-card-section>
                                </q-card>
                            </template>
                        </q-row>
                    </q-page-container>
                </div>

                <!-- Your Strategic Partner Section -->
                <q-card style="border-radius: 50px;" id="strategic-partner" class="q-mb-xl sectionContainer">
                    <q-card-section style="background-color: #FFFFFF;">
                        <h2 class="sectionTitle">Your Strategic Partner</h2>
                        <p class="sectionDetail">
                            With over 10 years of industry experience, we are dedicated to becoming your strategic
                            partner in achieving success. Our goal is to provide you with personalized support and
                            solutions that align with your objectives. Let us handle the details so you can focus on
                            what you do best.
                        </p>
                    </q-card-section>
                </q-card>

                <!-- Contact Section -->
                <q-card style="border-radius: 50px;" id="contact" class="q-mb-xl sectionContainer">
                    <q-card-section style="background-color: #FFFFFF;">
                        <h2 class="sectionTitle">Get in Touch</h2>
                        <p class="sectionDetail">
                            Have questions or need more information? We’d love to hear from you. Please fill out the
                            contact form below, and we will get back to you as soon as possible.
                        </p>
                        <q-form action="https://formsubmit.co/juliansalmuni@gmail.com" method="POST">
                            <q-input class="q-mb-sm" filled v-model="contactForm.name" name="Name" label="Name"
                                lazy-rules :rules="[
                                    val => val && val.length > 0 || 'Please enter your full name',
                                    val => /^[a-zA-Z\s]+$/.test(val) || 'Please enter a valid name (letters and spaces only)'
                                ]" />
                            <q-input class="q-mb-sm" filled v-model="contactForm.email" name="Email" label="Email"
                                lazy-rules :rules="[
                                    val => val && val.length > 0 || 'Please enter your e-mail address',
                                    val => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(val) || 'Please enter a valid email address'
                                ]" />
                            <q-input class="q-mb-sm" filled v-model="contactForm.phone" name="Phone" label="Phone"
                                lazy-rules :rules="[
                                    val => val && val.length > 0 || 'Please enter your phone number',
                                    val => /^[+]?[0-9\s()-]{7,}$/.test(val) || 'Please enter a valid phone number (digits and optional symbols only)'
                                ]" />
                            <q-input class="q-mb-sm" filled v-model="contactForm.message" name="Message" label="Message"
                                type="textarea" lazy-rules
                                :rules="[val => val && val.length > 0 || 'Please enter your message']" />

                            <input type="hidden" name="_next" value="http://localhost:8080/thank-you">
                            <input type="hidden" name="_subject" value="BAC New message">
                            <input type="hidden" name="_captcha" value="true">
                            <q-btn label="Send" type="submit" size="1rem" padding="sm xl" text-color="white"
                                style="background-color: #08529d;" class="q-mt-md" />
                            <q-btn
                                v-if="contactForm.name || contactForm.email || contactForm.phone || contactForm.message"
                                label="Reset" type="submit" size="1rem" padding="sm xl"
                                style="background-color: transparent; color: #08529d;" class="q-mt-md"
                                @click="resetForm" />

                        </q-form>
                    </q-card-section>
                </q-card>

                <!-- Footer -->
                <q-footer style="background-color: #00274d; height: 35px;" elevated class="text-center q-py-sm">
                    <div>Bison Atlas Consulting LLC | bisonatlas@atlas.com | 8 the Green, Dover, 19901, DE</div>
                </q-footer>
            </q-page>
        </q-page-container>
    </q-layout>

    <div v-if="isRedirecting" class="spinner-overlay">
        <q-spinner-cube size="7rem" style="color: #08529d;" />
    </div>
</template>

<script>
import { ref } from 'vue'

export default {
    setup() {
        return {
            isRedirecting: ref(false),
        }
    },
    data() {
        return {
            contactForm: {
                name: '',
                email: '',
                phone: '',
                message: ''
            },
            services: [
                {
                    id: '01',
                    name: 'Financial Consulting for Startups',
                    description: 'We specialize in designing robust financial processes and selecting optimal systems to support your startup’s financial and operational needs. Our services ensure efficient, cost-effective solutions that maintain strong internal controls, keep your books current, and provide accurate financial information.'
                },
                {
                    id: '02',
                    name: 'Bookkeeping',
                    description: 'Our monthly bookkeeping service takes the burden off your shoulders. Regardless of the volume of transactions, we manage your records meticulously, providing you with updated trial balances and financial statements each month. Stay focused on your business while we keep your finances in order.'
                },
                {
                    id: '03',
                    name: 'Catch-Up Bookkeeping',
                    description: 'If you’ve fallen behind on your bookkeeping, our catch-up service will get you back on track. We handle the backlog, ensuring your financial records are updated accurately and efficiently, so you can resume normal operations without hassle.'
                },
                {
                    id: '04',
                    name: 'Accounting',
                    description: 'We offer comprehensive accounting services, preparing financial statements in compliance with U.S. GAAP or IFRS standards. Our team delivers clear, accurate financial reporting to support your business decisions and ensure regulatory compliance.'
                },
                {
                    id: '05',
                    name: 'CFO Services',
                    description: 'Our customized CFO services provide strategic financial advice tailored to your business objectives. We offer in-depth financial analysis, performance reviews, and business planning to help you navigate complex decisions and drive your company’s growth.'
                },
                {
                    id: '06',
                    name: 'Virtual Support',
                    description: 'Enhance your efficiency with our virtual support services. Whether you need assistance with day-to-day tasks or specific projects, our team can help. We offer administrative support, stock management, marketing strategy advice, executive assistance, HR and onboarding, real estate management, and more.'
                }
            ]
        };
    },
    methods: {
        scrollTo(sectionId) {
            const element = document.getElementById(sectionId);
            if (element) {
                element.scrollIntoView({ behavior: 'smooth' });
            }
        },
        submitForm() {
            this.isRedirecting = true
        },
        resetForm() {
            this.contactForm = {
                name: '',
                email: '',
                phone: '',
                message: ''
            }
        },
        handleBeforeUnload() {
            setInterval(() => this.isRedirecting = true, 1000)
        }
    },
    mounted() {
        window.addEventListener('beforeunload', this.handleBeforeUnload);
    },
    beforeUnmount() {
        window.removeEventListener('beforeunload', this.handleBeforeUnload);
    },
};
</script>

<style>
.sectionContainer {
    padding: 30px 80px;
    border-radius: 50px;
}

.sectionTitle {
    font-weight: 700;
}

.sectionDetail {
    font-size: 26px;
}

.serviceTitle {
    color: #08529d;
    font-weight: 500;
}

.serviceDetail {
    font-size: 16px;
}

.heroContainer {
    background-color: #080C1E;
}

.heroSubtitle {
    color: #08529d;
}

body {
    font-family: 'Roboto', sans-serif;
    background-color: #f5f5f5;
}

h1 {
    color: #FFFFFF;
}

h2,
h3 {
    color: #00274d;
}

p {
    color: #555;
}

.q-card {
    background-color: #ffffff;
}

.q-btn {
    margin-right: 15px;
}

q-form {
    max-width: 600px;
    margin: 0 auto;
}

q-footer {
    color: white;
}

.spinner-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(255, 255, 255, 0.8);
    z-index: 9999;
}
</style>