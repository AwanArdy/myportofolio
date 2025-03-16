<template>
    <section id="projects" class="bg-[#F8F8F8] py-16">
        <div class="container mx-auto">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold text-gray-800">
                    Project & Skill
                </h2>
                <p class="text-gray-600">
                    Projek yang telah dibuat, bahasa dan framework.
                </p>
            </div>

            <div
                class="relative w-full flex justify-center items-center mt-20 mb-20"
            >
                <button
                    @click="prevCard"
                    class="absolute left-5 bg-gray-800 text-white p-3 rounded-full z-10"
                >
                    ◀
                </button>

                <div
                    class="relative w-[80%] flex justify-center items-center h-64"
                >
                    <div
                        v-for="(card, index) in cards"
                        :key="index"
                        class="absolute transition-all duration-500 ease-in-out transform"
                        :class="getCardClass(index)"
                    >
                        <div
                            class="rounded-md shadow-lg p-6 bg-white text-center w-96 h-72 flex flex-col justify-center items-center"
                        >
                            <img
                                :src="card.image"
                                alt="Project"
                                class="w-80 h-48 object-cover rounded-md"
                            />
                            <h3 class="mt-3 mb-1 text-xl font-bold text-black">
                                {{ card.title }}
                            </h3>
                            <p class="text-sm text-gray-600">
                                {{ card.description }}
                            </p>
                        </div>
                    </div>
                </div>

                <button
                    @click="nextCard"
                    class="absolute right-5 bg-gray-800 text-white p-3 rounded-full z-10"
                >
                    ▶
                </button>
            </div>
        </div>

        <section id="bahasa" class="pt-12 pb-12 dark:bg-dark">
            <div class="w-full px-4">
                <div class="mx-auto mb-16 text-center">
                    <h4 class="mb-2 text-4xl font-bold text-primary">
                        Bahasa & Framework
                    </h4>
                    <h2
                        class="mb-4 text-2xl font-semibold text-gray-800 sm:text-2xl lg:text-2xl"
                    >
                        Bahasa dan Framework yang sudah saya kuasai
                    </h2>
                </div>
            </div>

            <div class="w-full px-4">
                <div class="flex flex-wrap items-center justify-center">
                    <a
                        href="#"
                        class="mx-4 max-w-[120px] py-4 opacity-60 grayscale transition duration-500 hover:opacity-100 hover:grayscale-0 lg:mx-6 xl:mx-8"
                    >
                        <img src="../assets/img/nuxt.svg" alt="TypeScript" />
                    </a>
                    <a
                        href="#"
                        class="mx-4 max-w-[120px] py-4 opacity-60 grayscale transition duration-500 hover:opacity-100 hover:grayscale-0 lg:mx-6 xl:mx-8"
                    >
                        <img src="../assets/img/vue.svg" alt="HTML" />
                    </a>
                    <a
                        href="#"
                        class="mx-4 max-w-[120px] py-4 opacity-60 grayscale transition duration-500 hover:opacity-100 hover:grayscale-0 lg:mx-6 xl:mx-8"
                    >
                        <img src="../assets/img/js.svg" alt="CSS" />
                    </a>
                    <a
                        href="#"
                        class="mx-4 max-w-[120px] py-4 opacity-60 grayscale transition duration-500 hover:opacity-100 hover:grayscale-0 lg:mx-6 xl:mx-8"
                    >
                        <img
                            src="../assets/img/typescript.svg"
                            alt="JavaScript"
                        />
                    </a>
                    <a
                        href="#"
                        class="mx-4 max-w-[120px] py-4 opacity-60 grayscale transition duration-500 hover:opacity-100 hover:grayscale-0 lg:mx-6 xl:mx-8"
                    >
                        <img src="../assets/img/flutter.svg" alt="TypeScript" />
                    </a>
                    <a
                        href="#"
                        class="mx-4 max-w-[120px] py-4 opacity-60 grayscale transition duration-500 hover:opacity-100 hover:grayscale-0 lg:mx-6 xl:mx-8"
                    >
                        <img src="../assets/img/dart.svg" alt="TypeScript" />
                    </a>
                </div>
            </div>
        </section>
    </section>
</template>

<script>
export default {
    data() {
        return {
            cards: [
                {
                    title: "Projek A",
                    description: "Deskripsi A",
                    image: "https://res.cloudinary.com/dpnj5oclz/image/upload/f_auto,q_auto/v1/portofolio/ffrmnrdkyuw6us4yr7q5",
                },
                {
                    title: "Projek B",
                    description: "Deskripsi B",
                    image: "https://res.cloudinary.com/dpnj5oclz/image/upload/f_auto,q_auto/v1/portofolio/ffrmnrdkyuw6us4yr7q5",
                },
                {
                    title: "Projek C",
                    description: "Deskripsi C",
                    image: "https://res.cloudinary.com/dpnj5oclz/image/upload/f_auto,q_auto/v1/portofolio/ffrmnrdkyuw6us4yr7q5",
                },
            ],
            currentIndex: 0,
        };
    },
    methods: {
        prevCard() {
            this.currentIndex =
                (this.currentIndex - 1 + this.cards.length) % this.cards.length;
        },
        nextCard() {
            this.currentIndex = (this.currentIndex + 1) % this.cards.length;
        },
        getCardClass(index) {
            const totalCards = this.cards.length;

            if (index === this.currentIndex) {
                return "opacity-100 scale-100 z-10"; // Kartu tengah (aktif)
            } else if (
                index ===
                (this.currentIndex - 1 + totalCards) % totalCards
            ) {
                return "opacity-50 scale-100 -translate-x-60 z-0"; // Kartu kiri lebih ke kiri
            } else if (index === (this.currentIndex + 1) % totalCards) {
                return "opacity-50 scale-100 translate-x-60 z-0"; // Kartu kanan lebih ke kanan
            } else {
                return "opacity-0 hidden"; // Kartu lain tetap tersembunyi
            }
        },
    },
};
</script>

<style scoped>
.transition-transform {
    transition: all 0.5s ease-in-out;
}
</style>
