<template>
  <section class="box">
    <nav class="nav">
      <div>
        <div>
          <Input class="searchTree" placeholder="输入名称搜索" />
        </div>
        <ButtonGroup class="btngroup">
          <Button @click="operateItem(operate.add)">
            <Icon type="md-add" />
          </Button>
          <Button>
            <Icon type="ios-create" @click="operateItem(operate.update)" />
          </Button>
          <Button>
            <Icon type="ios-trash" @click="deleteItemTree()" />
          </Button>
        </ButtonGroup>
      </div>

      <div class="my-tree">
        <a-tree 
          v-if="treeData && treeData.length > 0"
          :checkable="false"
          :tree-data="treeData"
          class="menuTree"
          :autoExpandParent="true"
          :defaultExpandAll="true"
          :defaultExpandParent="true"
          @select="treeSelected"
        />
      </div>
    </nav>
    <div class="body">
      <header>
        <div>
          <ButtonGroup>
            <Button @click="operateItem(operate.add)">
              <Icon type="md-add" />添加
            </Button>
            <Button @click="operateItem(operate.update)">
              <Icon type="ios-create" />编辑
            </Button>
            <Button @click="deleteItem()">
              <Icon type="ios-trash" />删除
            </Button>
          </ButtonGroup>
        </div>
        <div class="searchdiv">
          <Input placeholder="根据名称搜索" class="searchInput" />
          <Button type="primary"> <Icon type="ios-search" />搜索 </Button>
        </div>
      </header>
      <article>
        <Table
          :columns="columns"
          :data="tableData"
          border
          tripe
          stripe
          class="table"
          @on-selection-change="CurrentRowEventArray"
        >
          <!-- @on-select-cancel="currentRowEventCancel" -->
          <!-- @on-select="currentRowEventArray" -->
        </Table>
        <page-component
          ref="PageInfo"
          :total="total"
          @PageChange="pageChange"
        ></page-component>
      </article>
    </div>
    <data-dictionary-operate ref="DataDictionaryInfo"></data-dictionary-operate>
    <delete-dialog ref="DeleteInfo"></delete-dialog>
  </section>
</template>
<script lang="ts" src="./data-dictionary-managerment.ts" />
<style lang="scss" src="./data-dictionary-managerment.scss" />
