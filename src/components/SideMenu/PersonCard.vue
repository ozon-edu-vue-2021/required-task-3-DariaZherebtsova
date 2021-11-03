<template>
    <div class="person">
        <div class="person__photo">
            <img
                :src="person.picture"
                alt="photo"
            />
        </div>
        <div class="person__info">
            <div class="person__info-name">
                <b>{{ person.name }} ({{ person.age }})</b>
            </div>

            <div class="person__info-email"><b>Почта:</b>{{ person.email }}</div>
            <div class="person__info-registration-date">
                <b>Дата регистрации:</b>{{ formatedDate }}
            </div>
            <div class="person__info-about"><b>О себе:</b>{{ person.about }}</div>
        </div>
    </div>
</template>

<script>
import { format, parseISO } from "date-fns";

export default {
    props: {
        person: {
            type: Object,
            default: null,
        },
    },
    computed: {
        formatedDate() {
            return format(parseISO(this.person.registered), "dd.MM.yyyy hh:mm");
            // return this.person.registered;
        },
    },
};
</script>

<style scoped>
.person {
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-gap: 8px;
}

.person__photo img {
    height: 50px;
    width: 50px;
    border-radius: 50%;
}

.person__info {
    display: grid;
    grid-gap: 12px;
}

.person__info-name {
    margin-bottom: 10px;
}

.person__info-email,
.person__info-registration-date,
.person__info-about {
    display: grid;
    grid-gap: 5px;
}
</style>
