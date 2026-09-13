<script setup lang="ts">
const email: string = "walden.hart.2003@gmail.com"
const linkedin: string = "https://www.linkedin.com/in/walden-hart/"
const github: string = "https://github.com/walden-hart"
</script>

<template>
    <v-container class="py-12">
        <v-row>
            <v-col cols="12" md="8">
                <h1 class="text-h3 font-weight-bold mb-6">Contact Me</h1>

                <v-card>
                    <v-card-text>
                        <p class="text-body-1">
                            I'm always interested in discussing software engineering, full-stack development, and security-focused projects.
                            Whether you're reaching out about an opportunity, have a question, or just want to say hello, feel free to contact me.

                            You can reach me at:
                        </p>
                        <v-list lines="one" class="text-body-1">
                            <v-list-item :href="`mailto:${email}`" target="_blank" rel="noopener">
                                <v-list-item-title>Email</v-list-item-title>
                                <v-list-item-subtitle>{{ email }}</v-list-item-subtitle>
                            </v-list-item>
                            <v-list-item :href="linkedin" target="_blank" rel="noopener">
                                <v-list-item-title>LinkedIn</v-list-item-title>
                                <v-list-item-subtitle>{{ linkedin }}</v-list-item-subtitle>
                            </v-list-item>
                            <v-list-item :href="github" target="_blank" rel="noopener">
                                <v-list-item-title>Github</v-list-item-title>
                                <v-list-item-subtitle>{{ github }}</v-list-item-subtitle>
                            </v-list-item>
                        </v-list>
                        <p class="text-body-1">
                            I look forward to hearing from you.
                        </p>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<style scoped></style>