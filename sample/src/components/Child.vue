<template>
<div>
    <header>
        <slot name="header">Default data</slot>
    </header>
    <content>
        <slot name="main">Default data</slot>
    </content>
    <footer>
        <slot name="footer">Default data</slot>
    </footer>
</div>
</template>

<script>
export default {
    name: "Child"
}
</script>
