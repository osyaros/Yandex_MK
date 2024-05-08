<script>
    export let status;
    export let status_color;
</script>

<style>
    .status{
        display: inline-flex;
        width:  max-content;
        padding: 6px 30px;
        justify-content: center;
        align-items: center;
        gap: 10px;
        border-radius: 40px;
        border: 1px solid;
        font-family: "Yandex Sans Text";
        font-size: 15px;
        font-style: normal;
        font-weight: 500;
        line-height: 21px /* 140% */;
    }
</style>
<div class="status" style="color:{status_color}; border-color:{status_color};">
    <span>{status}</span>
</div>