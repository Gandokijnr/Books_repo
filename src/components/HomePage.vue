<template>
    <div class="d-flex flex-column align-items-center justify-content-center gap-4">
        <h2 class="text-center mt-4">{{ Listitems }}</h2>
        <ul class="w-50 text-center">
            <li class="list-group-item shadow rounded p-3 mt-2 fw-bold"  :class="{ 'bg-green': item.isFavourite }" v-for="item in Items" :key="item.id" @click="toggleFavourite(item)">
                {{ item.title }}
                <small>by {{ item.author }}</small><br>
                <small>{{ item.year }}</small><br>
                <small>{{ item.genre }}</small>
            </li>
        </ul>
    </div>
</template>

<script>    
import Swal from 'sweetalert2'

    export default {
        data() {
            return {
                Listitems: "List of books",
                Items: [
                    { id: 1, title: "To Kill a Mockingbird", author: "Harper Lee", year: 1960, genre: "Fiction", isFavourite: false },
                    { id: 2, title: "1984", author: "George Orwell", year: 1949, genre: "Dystopian", isFavourite: false },
                    { id: 3, title: "The Great Gatsby", author: "F. Scott Fitzgerald", year: 1925, genre: "Fiction", isFavourite: false },
                    { id: 4, title: "The Catcher in the Rye", author: "J.D. Salinger", year: 1951, genre: "Fiction", isFavourite: false },
                    { id: 5, title: "Pride and Prejudice", author: "Jane Austen", year: 1813, genre: "Romance", isFavourite: false }
                ]
            }
        },
        methods: {
        toggleFavourite(item) {
            if (item.isFavourite) {
                item.isFavourite = false;
            }else{
            Swal.fire({
                title: `Add ${item.author} to favorites?`,
                text: `Do you want to add "${item.title}" by ${item.author} to your favorites?`,
                icon: 'question',
                showCancelButton: true,
                confirmButtonText: 'Yes',
                cancelButtonText: 'No',
                confirmButtonColor: '#3085d6',
                cancelButtonColor: '#d33',
            }).then((result) => {
                if (result.isConfirmed) {
                    item.isFavourite = !item.isFavourite;
                    if (item.isFavourite) {
                        Swal.fire(
                            'Added!',
                            `${item.title} by ${item.author} has been added to your favorites.`,
                            'success'
                        )
                    }
                }
            })
        }
    }
    }
}
</script>

<style scoped>
    .bg-green {
        background-color: green;
        color: white;
    }
</style>
