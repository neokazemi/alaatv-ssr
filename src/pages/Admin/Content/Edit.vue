<template>
  <entity-edit
    v-model:value="inputs"
    title="اطلاعات محتوا"
    :api="api"
    :entity-id-key="entityIdKey"
    :entity-param-key="entityParamKey"
    :show-route-name="showRouteName"
    :before-load-input-data="getCategories"
  />
</template>

<script>
import { EntityEdit } from 'quasar-crud'
import API_ADDRESS from 'src/api/Addresses'
export default {
  name: 'Edit',
  components: { EntityEdit },
  methods: {
    getCategories (val) {
      console.log('val', val)
      val.data.description.short = val.data.title
      console.log('val2', val)
      // this.testMethod1()
    },
    testMethod1 () {
      console.log('skjdfhlksdjfksjfhksd')
    }
  },
  data () {
    return {
      expanded: true,
      api: API_ADDRESS.content.edit.base,
      entityIdKey: 'id',
      entityParamKey: 'id',
      showRouteName: 'Admin.Content.Show',
      inputs: [
        { type: 'file', name: 'photo', responseKey: 'data.photo', size: '250px', col: 'col-md-3' },
        { type: 'space', col: 'col-md-12' },
        { type: 'optionGroupRadio', name: 'is_free', responseKey: 'data.is_free', label: '', col: 'col-md-3', options: [{ label: 'رایگان باشد', value: 1 }, { label: 'رایگان نباشد', value: 0 }] },
        { type: 'optionGroupRadio', name: 'enable', options: [{ label: 'غیرفعال', value: 0 }, { label: 'فعال', value: 1 }], responseKey: 'data.enable', label: 'وضعیت', col: 'col-md-3' },
        { type: 'optionGroupRadio', name: 'discount', options: [{ label: 'عدم نمایش', value: 0 }, { label: 'نمایش', value: 1 }], responseKey: 'data.discount', label: 'نمایش', col: 'col-md-3' },
        { type: 'optionGroupCheckbox', multiple: true, options: [{ label: 'درج کیفیت hq', value: 0 }, { label: 'درج کیفیت HD', value: 1 }, { label: 'درج کیفیت 240p', value: 2 }], name: 'enable', value: [1], label: 'کیفیت محتوا', col: 'col-md-3' },
        { type: 'file', name: 'photo', label: 'کیفیت عالی', responseKey: 'data.photo', size: '250px', col: 'col-md-4' },
        { type: 'file', name: 'photo', responseKey: 'data.photo', label: 'کیفیت خوب', size: '250px', col: 'col-md-4' },
        { type: 'file', name: 'photo', responseKey: 'data.photo', label: 'کیفیت متوسط', size: '250px', col: 'col-md-4' },
        { type: 'input', name: 'id', responseKey: 'data.id', label: 'نمایان شدن برای کاربران', col: 'col-md-3' },
        { type: 'input', name: 'id', responseKey: 'data.id', label: 'تاریخ درج', col: 'col-md-3' },
        { type: 'input', name: 'order', responseKey: 'data.order', label: 'آیدی دبیر', col: 'col-md-3' },
        { type: 'input', name: 'redirect_url', responseKey: 'data.redirect_url', label: 'آدرس ریدایرکت', col: 'col-md-3' },
        { type: 'select', name: 'redirect_code', responseKey: 'data.product_type.display_name', options: [{ label: '301 (دائمی)', value: 301 }, { label: '302 (موقتی)', value: 302 }], label: 'کد ریدایرکت', col: 'col-md-3' },
        { type: 'input', name: 'order', responseKey: 'data.order', label: 'ترتیب', col: 'col-md-3' },
        { type: 'select', name: 'content_type_id', value: null, options: [{ label: 'ویدئو', value: 0 }, { label: 'جزوه', value: 8 }, { label: 'مقاله', value: 3 }], label: 'نوع محتوا', col: 'col-md-3' },
        { type: 'select', name: 'attribute_set', responseKey: 'data.attribute_set.id', label: 'سکشن محتوا', col: 'col-md-3', options: [{ label: 'اردو', value: 1 }, { label: 'همایش', value: 2 }, { label: 'فیلم استودیو', value: 3 }, { label: 'جزوه درس', value: 4 }, { label: 'کتاب', value: 5 }, { label: 'پیش فرض', value: 6 }, { label: 'محصول اشتراک', value: 7 }, { label: 'آزمون', value: 8 }] },
        { type: 'input', name: 'title', responseKey: 'data.title', label: 'نام*', col: 'col-md-3' },
        { type: 'input-editor', name: 'short_description', responseKey: 'data.description.short', label: 'توضیحات', col: 'col-md-12' },
        { type: 'select', name: 'tags', options: [], responseKey: 'data.tags', multiple: true, useChips: true, createNewValue: true, label: 'تگ ها', col: 'col-md-6' },
        { type: 'input', name: 'tags-title', responseKey: 'data.tags.title', label: 'متن تگ ها', col: 'col-md-6' },
        { type: 'input', name: 'order', responseKey: '', label: 'ابر عنوان', col: 'col-md-6' },
        { type: 'input', name: 'order', responseKey: '', label: 'ابر توضیح', col: 'col-md-6' }
      ]
    }
  },
  created () {
    this.api += '/' + this.$route.params.id
  }
}
</script>

<style scoped>

</style>
