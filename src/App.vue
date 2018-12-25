<template>
    <div id="app">
        <Form :model="formItem" :label-width="120">
            <FormItem label="说到">
                <Input v-model="formItem.shuo" placeholder=""></Input>
            </FormItem>
            <FormItem label="想起">
                <Input v-model="formItem.xiang" placeholder=""></Input>
            </FormItem>
            <FormItem label="">
                <Input ref="resultText" type="textarea" v-model="resultText" readonly :rows=5></Input>
            </FormItem>
            <FormItem label="" class="form-item-action">
                <Button type="primary" size="large" @click="copy">复制</Button>
            </FormItem>
        </Form>
    </div>
</template>
<script>
export default {
    data () {
        return {
            formItem: {
                shuo: 'Ant Design 圣诞彩蛋',
                xiang: '筋斗云和孙悟空'
            }
        }
    },
    computed: {
        resultText () {
            return `说到${this.formItem.shuo}，我就想起${this.formItem.xiang}，明年年初，中美合拍的西游记即将正式开机，我继续扮演美猴王孙悟空，我会用美猴王艺术形象努力创造一个正能量的形象，文体两开花，弘扬中华文化，希望大家多多关注。`
        }  
    },
    methods: {
        copy () {
            document.querySelector('textarea').select()
            document.execCommand('copy')
            this.$Message.info('复制成功');
        }
    }
}
</script>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.ivu-form
{
    position: absolute;
    top: 40%;
    left: 50%;
    width: 800px;
    transform: translate(-50%, -50%);
}
.form-item-action
{
    text-align: right;
}
</style>
