<script>
  import { Button } from "@budibase/bbui"
  import { goto } from "@roxi/routify"
  import { auth, admin } from "stores/portal"
</script>

{#if $admin.cloud && $auth?.user?.accountPortalAccess}
  <Button
    cta
    size="S"
    on:click
    on:click={() => {
      window.open($admin.accountPortalUrl + "/portal/upgrade", "_blank")
    }}
  >
    Upgrade
  </Button>
{:else if !$admin.cloud && $auth.isAdmin}
  <Button
    cta
    size="S"
    on:click={() => $goto("/builder/portal/account/upgrade")}
    on:click
  >
    Upgrade
  </Button>
{/if}
