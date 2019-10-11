<template>
    <div>
        <strong>Points</strong> <span>{{points}}</span>
        <!--pre>
            {{ $props }}
        </pre-->
    </div>
</template>

<script>
export default {
    name: "points.movies",
    props: ['points']
}
 </script>
