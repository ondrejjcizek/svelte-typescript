<script lang="ts">
    interface Person {
        name: string;
        age: number;

        greet(phrase: string): void;
    }

    let user1: Person;

    user1 = {
        name: 'Ondrej',
        age: 26,
        greet(phrase: string) {
            console.log(phrase + ' ' + this.name);
        }
    }

    user1.greet('Hi there - I am')
</script>


<h1>Interfaces</h1>