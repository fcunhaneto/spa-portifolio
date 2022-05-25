<template>
    <Head title="Welcome" />
    <div>
        <Section class="grid grid-cols-2 text-right bg-gray-800 text-gray-300">
            <div>
                <jet-application-mark class="h-12 w-auto"></jet-application-mark>
            </div>
            <div v-if="canLogin">
                <Link v-if="$page.props.user" :href="route('dashboard')" class="text-sm underline">
                    Dashboard
                </Link>

                <template v-else>
                    <Link :href="route('login')" class="text-base underline">
                        Log in
                    </Link>

                    <Link v-if="canRegister" :href="route('register')" class="text-base underline place-self-end ml-4">
                        Register
                    </Link>
                </template>
            </div>
        </Section>
        <Section class="bg-gray-800 h-screen">
            <div class="h-2/3 flex flex-wrap content-between pb-36">
                <p class="border-b-2 border-gray-400 font-bold text-2xl text-gray-300 uppercase pb-3">
                    Olá! Meu nome é Francisco. Sou Engenheiro de Software e terei prazer em trabalhar com vocês.
                </p>
                <div class="flex items-end border-b-2 bg-gray-500 pb-2">
                    <p class="font-bold mr-5 text-gray-500 text-xl">
                        Quer saber mais?
                    </p>
                    <jet-button class="bg-green-400 font-bold text-sm text-gray-800 hover:bg-green-800">
                        Iniciar um  chat
                    </jet-button>
                </div>

            </div>
            <div class="text-center">
                <a class="animate-pulse mt-3 text-gray-300 text-9xl" href="#skills">&#8675;</a>
            </div>
        </Section>

        <Section id="skills" class="bg-gray-200 text-gray-800 h-screen">
            <h2 class="text-6xl font-bold pt-3">Skills</h2>
            <div class="grid grid-cols-2">
                <div v-for="skill in skills">
                    <Skills :background="skill.color">
                        {{ skill.name}}
                    </Skills>
                </div>
            </div>

            <div class="flex justify-center mt-10">
                <jet-button class="bg-indigo-800 font-bold text-sm text-gray-200 hover:bg-indigo-600">
                    Entre em contato
                </jet-button>
            </div>

        </Section>

        <Section class="bg-gray-600 text-gray-200 h-screen">
            <h2 class="text-6xl font-bold pt-3">Projetos</h2>
            <div class="flex justify-center mt-10">
                <jet-button class="bg-purple-100 font-bold text-sm text-gray-800 hover:bg-purple-200">
                    Saiba mais
                </jet-button>
            </div>
        </Section>

        <Section class="flex justify-between bg-gray-800 text-gray-300 text-xl pb-16">
            <p>&copy; Francisco Cunha Neto</p>
            <div class="flex justify-evenly items-center">
                Github
                Twitter
                StackOverflow
            </div>
        </Section>
    </div>
</template>
<script>
import { defineComponent } from 'vue'
import { Head, Link } from '@inertiajs/inertia-vue3';

import JetApplicationMark from '../Jetstream/ApplicationMark';
import JetButton from '../Jetstream/Button';

import Section from "../Components/Section";
import Skills from "../Components/Skills";

export default defineComponent({
    components: {
        Head,
        Link,
        JetApplicationMark,
        Section,
        JetButton,
        Skills,
    },

    props: {
        canLogin: Boolean,
        canRegister: Boolean,
        skills: Object,
    },
});

</script>
