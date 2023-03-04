<template>
    <div class="alert alert-success" role="alert">
        <slot name="titulo"></slot>
        <hr>

        <slot name="descricao"></slot>
        <hr>
        
        <slot></slot>
      </div>
</template>

<script>
export default {
    name: 'AlertaComum'
}
</script>