# zx_bti_create

## NAME

bti_create - create a new bus transaction initiator

## SYNOPSIS

```
#include <zircon/syscalls.h>

zx_status_t zx_bti_create(zx_handle_t iommu, uint64_t bti_id, zx_handle_t* out);

```

## DESCRIPTION

**bti_create**() creates a new [bus transaction initiator](../objects/bus_transaction_initiator.md)
given a handle to an IOMMU and a hardware transaction identifier for a device
downstream of that IOMMU.

Upon success a handle for the new BTI is returned.  This handle will have rights
**ZX_RIGHT_READ**, **ZX_RIGHT_MAP**, **ZX_RIGHT_DUPLICATE**, and
**ZX_RIGHT_TRANSFER**.

## RETURN VALUE

**bti_create**() returns ZX_OK and a handle to the new BTI
(via *out*) on success.  In the event of failure, a negative error value
is returned.

## ERRORS

**ZX_ERR_BAD_HANDLE**  *iommu* is not a valid handle.

**ZX_ERR_WRONG_TYPE**  *iommu* is not an iommu handle.

**ZX_ERR_INVALID_ARGS**  *bti_id* is invalid on the given IOMMU,
or *out* is an invalid pointer.

**ZX_ERR_NO_MEMORY**  (Temporary) Failure due to lack of memory.

## SEE ALSO

[bti_pin](bti_pin.md),
[bti_unpin](bti_unpin.md).