<script setup lang="ts">
  import UserType from "../model/user";
  interface UserCardListProps {
    loading:boolean;
    userList:UserType[]; /*此属性为数组类型*/
  }
  const props = withDefaults(defineProps<UserCardListProps>(),{
    loading:true,
    //@ts-ignore
    userList:[] as UserType[], /*设置userList默认为空数组*/
  });
</script>

<template>
  <van-skeleton title avatar :row="3" :loading="props.loading" v-for="user in props.userList">
    <van-card
              :title="`${user.username} (${user.planetCode})`"
              :desc=user.profile
              :thumb=user.avatarUrl
    >
      <template #tags>
        <van-tag plain type="primary" v-for="tag in user.tags" style="margin-right: 8px;margin-top: 8px">
          {{tag}}
        </van-tag>
      </template>
      <template #footer>
        <van-button size="mini">联系我</van-button>
      </template>
    </van-card>
  </van-skeleton>

</template>

<style scoped>

</style>