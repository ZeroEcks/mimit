<script setup lang="ts">
const props = defineProps(['data'])
console.log(props.data)
</script>

<template>
    <article class="card">
        <header>
            <img v-bind:src="props.data?.portraitWikiUrl">
            <h3><a v-bind:href="props.data?.wikiUrl">{{ props.data?.name }}</a></h3>
            <footer>
                <div>
                    <div v-bind:class="'button stack type type-' + tp.name.toLowerCase()" v-for="tp in props.data?.types">
                        <img class="type-icon" v-bind:src="'https://temtem-api.mael.tech' + tp.icon" />
                        {{ tp.name }}
                    </div>
                </div>
                <div>
                    <div>4x:
                        <span v-for="weakness in Object.keys(props.data?.weaknesses)">
                            <span v-if="props.data?.weaknesses[weakness] === 4">
                                <img class="type-icon" v-bind:src="'https://temtem-api.mael.tech/images/icons/types/' + weakness + '.png'"/>
                                {{ weakness }} &nbsp; </span>
                        </span>
                    </div>
                    <div>2x:
                        <span v-for="weakness in Object.keys(props.data?.weaknesses)">
                            <span v-if="props.data?.weaknesses[weakness] === 2">
                                <img class="type-icon" v-bind:src="'https://temtem-api.mael.tech/images/icons/types/' + weakness + '.png'"/>
                                {{ weakness }} &nbsp;</span>
                        </span>
                    </div>
                    <div>0.5x:
                        <span v-for="weakness in Object.keys(props.data?.weaknesses)">
                            <span v-if="props.data?.weaknesses[weakness] === 0.5">
                                <img class="type-icon" v-bind:src="'https://temtem-api.mael.tech/images/icons/types/' + weakness + '.png'"/>
                                {{ weakness }} &nbsp;</span>
                        </span>
                    </div>
                    <div>0.25x:
                        <span v-for="weakness in Object.keys(props.data?.weaknesses)">
                            <span v-if="props.data?.weaknesses[weakness] === 0.25">
                                <img class="type-icon" v-bind:src="'https://temtem-api.mael.tech/images/icons/types/' + weakness + '.png'"/>
                                {{ weakness }} &nbsp;</span>
                        </span>
                    </div>
                </div>
            </footer>
        </header>
    </article>
</template>

<style scoped>
.type-icon {
    max-width: 18px;
}

.type {
    max-width: 128px;
}

.type-neutral {
    color: black;
    background-color: #E6F6F4
}

.type-wind {
    background-color: #0FF8B2
}

.type-earth {
    background-color: #BB7A5B
}

.type-water {
    background-color: #45CCFD
}

.type-fire {
    background-color: #E95C4E
}

.type-nature {
    background-color: #ADDE77
}

.type-electric {
    background-color: #FEE174
}

.type-mental {
    background-color: #BB6E9D
}

.type-digital {
    background-color: #A6C0C3
}

.type-melee {
    background-color: #F29364
}

.type-crystal {
    background-color: #EA4968
}

.type-toxic {
    background-color: #5A565C
}</style>